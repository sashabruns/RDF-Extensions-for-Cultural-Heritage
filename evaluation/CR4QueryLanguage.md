## Example
texttextext
```
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX : <http://example.org/>
```
#### Named Graphs (Query)
```

```
#### Named Graphs 
```
GRAPH :graph1 {
  :street1 rdfs:label "Roßmarkt" .
  :street2 rdfs:label "Zisselgasse" .
  :street3 rdfs:label "auf dem Gras" .
  :street4 rdfs:label "Spiegelgasse" .
}
:graph1 :validIn "[0,1809]" .

GRAPH :graph2 {
  :street1 rdfs:label "Adlerstraße" .
  :street2 rdfs:label "Albrecht Dürer-Straße" .
  :street3 rdfs:label "Am Gräslein" .
  :street4 rdfs:label "Äussere Laufer-Gasse" .
}
:graph2 :validIn "[1809, now]" .
GRAPH :graph3 {
  :person1 :livesIn :street1 .
}
:graph3 :validIn "1908" .

GRAPH :graph4 {
  :person1 :livesIn :street2 .
}
:graph4 :validIn "1910" .

GRAPH :graph5 {
  :person1 :livesIn :street3 .
}
:graph5 :validIn "1921" .

GRAPH :graph6 {
  :person1 :livesIn :street4 .
}
:graph6 :validIn "1940" .

:person1 rdfs:label "Ida Bachmann" .
```
#### tRDF

```
:statement1 rdf:subject :street1 ;
    rdf:predicate rdfs:label ;
    rdf:object "Roßmarkt" ;
    :validIn "[0,1809]" .

:statement2 rdf:subject :street1 ;
    rdf:predicate rdfs:label ;
    rdf:object "Adlerstraße" ;
    :validIn "[1809, now]" .

:statement3 rdf:subject :street2 ;
    rdf:predicate rdfs:label ;
    rdf:object "Zisselgasse" ;
    :validIn "[0,1809]" .

:statement4 rdf:subject :street2 ;
    rdf:predicate rdfs:label ;
    rdf:object "Albrecht Dürer-Straße" ;
    :validIn "[1809, now]" .

:statement5 rdf:subject :street3 ;
    rdf:predicate rdfs:label ;
    rdf:object "auf dem Gras" ;
    :validIn "[0,1809]" .

:statement6 rdf:subject :street3 ;
    rdf:predicate rdfs:label ;
    rdf:object "Am Gräslein" ;
    :validIn "[1809, now]" .

:statement7 rdf:subject :street4 ;
    rdf:predicate rdfs:label ;
    rdf:object "Spiegelgasse" ;
    :validIn "[0,1809]" .

:statement8 rdf:subject :street4 ;
    rdf:predicate rdfs:label ;
    rdf:object "Äussere Laufer-Gasse" ;
    :validIn "[1809, now]" .

:statement9 rdf:subject :person1 ;
    rdf:predicate :livesIn ;
    rdf:object :street1 ;
    :validIn "1908" .

:statement10 rdf:subject :person1 ;
    rdf:predicate :livesIn ;
    rdf:object :street2 ;
    :validIn "1910" .

:statement11 rdf:subject :person1 ;
    rdf:predicate :livesIn ;
    rdf:object :street3 ;
    :validIn "1921" .

:statement12 rdf:subject :person1 ;
    rdf:predicate :livesIn ;
    rdf:object :street4 ;
    :validIn "1940" .

:person1 rdfs:label "Ida Bachmann" .
```
#### RDF* (Query)
```
SELECT ?street ?residencePeriod ?streetName ?nameValidPeriod
WHERE {
    ?person rdfs:label "Ida Bachmann" .
    <<?person :livesIn ?street>> :validIn ?residencePeriod .
    <<?street rdfs:label ?streetName>> :validIn ?nameValidPeriod .
}
ORDER BY ?residencePeriod ?nameValidPeriod
```
#### RDF* (data)
```
<<:street1 rdfs:label "Roßmarkt">:validIn "[0,1809]">  .
<<:street1 rdfs:label "Adlerstraße"> :validIn "[1809, now]"> .

<<:street2 rdfs:label "Zisselgasse"> :validIn "[0,1809]"> .
<<:street2 rdfs:label "Albrecht Dürer-Straße"> :validIn "[1809, now]"> .

<<:street3 rdfs:label "auf dem Gras">> :validIn "[0,1809]"> .
<<:street3 rdfs:label "Am Gräslein">> :validIn "[1809, now]"> .

<<:street4 rdfs:label "Spiegelgasse">> :validIn "[0,1809]"> .
<<:street4 rdfs:label "Äussere Laufer-Gasse">> :validIn "[1809, now]"> .

<<:person1 :livesIn :street1> :validIn "1908"> .
<<:person1 :livesIn :street2> :validIn "1910"> .
<<:person1 :livesIn :street3> :validIn "1921"> .
<<:person1 :livesIn :street4> :validIn "1940"> .

:person1 rdfs:label "Ida Bachmann" .
```
#### 4D Fluents
```
:street1_0_1809 rdfs:label "Roßmarkt" ;
    :validIn "[0,1809]" ;
    :timeSliceOf :street1 .

:street1_1809_present rdfs:label "Adlerstraße" ;
    :validIn "[1809, now]" ;
    :timeSliceOf :street1 .

:street2_0_1809 rdfs:label "Zisselgasse" ;
    :validIn "[0,1809]" ;
    :timeSliceOf :street2 .

:street2_1809_present rdfs:label "Albrecht Dürer-Straße" ;
    :validIn "[1809, now]" ;
    :timeSliceOf :street2 .

:street3_0_1809 rdfs:label "auf dem Gras" ;
    :validIn "[0,1809]" ;
    :timeSliceOf :street3 .

:street3_1809_present rdfs:label "Am Gräslein" ;
    :validIn "[1809, now]" ;
    :timeSliceOf :street3 .

:street4_0_1809 rdfs:label "Spiegelgasse" ;
    :validIn "[0,1809]" ;
    :timeSliceOf :street4 .

:street4_1809_present rdfs:label "Äussere Laufer-Gasse" ;
    :validIn "[1809, now]" ;
    :timeSliceOf :street4 .

:person1_1908 :livesIn :street1_1908 ;
    :validIn "1908" ;
    :timeSliceOf :person1 .

:person1_1910 :livesIn :street2_1910 ;
    :validIn "1910" ;
    :timeSliceOf :person1 .

:person1_1921 :livesIn :street3_1921 ;
    :validIn "1921" ;
    :timeSliceOf :person1 .

:person1_1940 :livesIn :street4_1940 ;
    :validIn "1940" ;
    :timeSliceOf :person1 .

:street1_1908 :validIn "1908" ;
    :timeSliceOf :street1 .

:street2_1910 :validIn "1910" ;
    :timeSliceOf :street2 .

:street3_1921 :validIn "1921" ;
    :timeSliceOf :street3 .

:street4_1940 :validIn "1940" ;
    :timeSliceOf :street4 .

:person1 rdfs:label "Ida Bachmann" .
```
#### Singleton Properties:

```

:label_0_1809 rdf:singletonPropertyOf rdfs:label ;
    :validIn "[0,1809]" .

:label_1809_present rdf:singletonPropertyOf rdfs:label ;
    :validIn "[1809, now]" .

:street1 :label_0_1809 "Roßmarkt" .
:street1 :label_1809_present "Adlerstraße" .

:label_0_1809_2 rdf:singletonPropertyOf rdfs:label ;
    :validIn "[0,1809]" .

:label_1809_present_2 rdf:singletonPropertyOf rdfs:label ;
    :validIn "[1809, now]" .

:street2 :label_0_1809_2 "Zisselgasse" .
:street2 :label_1809_present_2 "Albrecht Dürer-Straße" .

:label_0_1809_3 rdf:singletonPropertyOf rdfs:label ;
    :validIn "[0,1809]" .

:label_1809_present_3 rdf:singletonPropertyOf rdfs:label ;
    :validIn "[1809, now]" .

:street3 :label_0_1809_3 "auf dem Gras" .
:street3 :label_1809_present_3 "Am Gräslein" .

:label_0_1809_4 rdf:singletonPropertyOf rdfs:label ;
    :validIn "[0,1809]" .

:label_1809_present_4 rdf:singletonPropertyOf rdfs:label ;
    :validIn "[1809, now]" .

:street4 :label_0_1809_4 "Spiegelgasse" .
:street4 :label_1809_present_4 "Äussere Laufer-Gasse" .

:livesIn_1908 rdf:singletonPropertyOf :livesIn ;
    :validIn "1908" .

:livesIn_1910 rdf:singletonPropertyOf :livesIn ;
    :validIn "1910" .

:livesIn_1921 rdf:singletonPropertyOf :livesIn ;
    :validIn "1921" .

:livesIn_1940 rdf:singletonPropertyOf :livesIn ;
    :validIn "1940" .

:person1 :livesIn_1908 :street1 .
:person1 :livesIn_1910 :street2 .
:person1 :livesIn_1921 :street3 .
:person1 :livesIn_1940 :street4 .

:person1 rdfs:label "Ida Bachmann" .
```
#### N-ary:
```
:person1 rdfs:label "Ida Bachmann" .

:street1_label1 :appliesTo :street1 ;
    :streetName "Roßmarkt" ;
    :validIn "[0,1809]" .

:street1_label2 :appliesTo :street1 ;
    :streetName "Adlerstraße" ;
    :validIn "[1809, now]" .

:street2_label1 :appliesTo :street2 ;
    :streetName "Zisselgasse" ;
    :validIn "[0,1809]" .

:street2_label2 :appliesTo :street2 ;
    :streetName "Albrecht Dürer-Straße" ;
    :validIn "[1809, now]" .

:street3_label1 :appliesTo :street3 ;
    :streetName "auf dem Gras" ;
    :validIn "[0,1809]" .

:street3_label2 :appliesTo :street3 ;
    :streetName "Am Gräslein" ;
    :validIn "[1809, now]" .

:street4_label1 :appliesTo :street4 ;
    :streetName "Spiegelgasse" ;
    :validIn "[0,1809]" .

:street4_label2 :appliesTo :street4 ;
    :streetName "Äussere Laufer-Gasse" ;
    :validIn "[1809, now]" .

:person_location1 :appliesTo :person1 ;
    :location :street1 ;
    :validIn "1908" .

:person_location2 :appliesTo :person1 ;
    :location :street2 ;
    :validIn "1910" .

:person_location3 :appliesTo :person1 ;
    :location :street3 ;
    :validIn "1921" .

:person_location4 :appliesTo :person1 ;
    :location :street4 ;
    :validIn "1940" .
```    
