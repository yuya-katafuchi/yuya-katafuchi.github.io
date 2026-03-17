---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% include base_path %}

{% assign pubs = site.publications | sort: "date" | reverse %}
{% assign pubs_by_year = pubs | group_by: "year" %}

{% for year in pubs_by_year %}
<h2>{{ year.name }}</h2>

{% for post in year.items %}
<div class="publication-entry{% if post.image %} publication-entry--with-image{% endif %}">
<div class="publication-entry__text">
<p class="publication-entry__citation">
{{ post.authors | markdownify | remove: '<p>' | remove: '</p>' }}
({{ post.year }}).
<a href="{{ post.paperurl }}">{{ post.title }}</a>.
{{ post.journal | markdownify | remove: '<p>' | remove: '</p>' }}
</p>

{% if post.japanese_title %}
<p class="publication-entry__sub">
<a href="{{ post.japanese_url }}">{{ post.japanese_title }}</a>
</p>
{% endif %}

{% if post.preprint %}
<p class="publication-entry__sub">
<a href="{{ post.preprint }}">Preprint</a>
</p>
{% endif %}

{% if post.press %}
<p class="publication-entry__sub">
Press:
{{ post.press | markdownify | remove: '<p>' | remove: '</p>' }}
</p>
{% endif %}
</div>

{% if post.image %}
<div class="publication-entry__image">
<img src="{{ post.image | prepend: base_path }}" alt="{{ post.title }}">
</div>
{% endif %}
</div>
{% endfor %}
{% endfor %}