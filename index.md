---
layout: default
rdf_prefix_path: _data/prefixes.pref
---

# Personen

{% assign persons = page.rdf | sparql_query: "select ?person {?person a foaf:Person }" %}
{% for row in persons %}
* [{{ row.person | rdf_property: "foaf:name" }}]({{ row.person.page_url }}) ({{ row.person | rdf_inverse_property: "schema:performer", true | size }})
{% endfor %}
