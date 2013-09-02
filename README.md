Jekyll-DB
=========

An easy way to use Jekyll and Github Pages as a "database".

See it in action: [http://rypan.github.io/jekyll-db](http://rypan.github.io/jekyll-db)

### Use posts as entries

```
---
layout: entry
company-name: AchieveMint
city: San Francisco
state: California
employees: 100

categories:
- startup

tags:
- wellness
- consumer
- employer
---
```

### Output your fields in a table

```
<tbody class="list">
{% for post in site.posts %}
	<tr>
		<td class="name">{{ post.company-name }}</td>
		<td class="city">{{ post.city }}</td>
		<td class="category">{{ post.categories }}</td>
		<td class="tags">{{ post.tags | array_to_sentence_string }}</td>
	</tr>
{% endfor %}
</tbody>
```

### Index the appropriate fields

```
<script type="text/javascript">

var options = {
  valueNames: ['name', 'city', 'category', 'tags']
};

var entryList = new List('entry-list', options);

</script>
```

### Output your data as JSON

```
---
layout: none
---
[{% for post in site.posts %}{
	"company-name": "{{post.company-name}}",
	"city": "{{post.city}}",
	"state": "{{post.state}}",
	"employees": "{{post.employees}}",
	"tags": "{{ post.tags | array_to_sentence_string }}",
	"categories": "{{post.categories}}"
}{% if forloop.rindex0 > 0 %},{% endif %}{% endfor %}]
```

### Credits

All the credits go to [Jekyll](http://jekyllrb.com/), [ListJS](http://listjs.com/) + [Bootstrap](http://getbootstrap.com/). I just pulled the pieces together.
