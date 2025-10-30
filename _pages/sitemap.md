---
layout: archive
title: "Sitemap"
permalink: /sitemap/
author_profile: true
---
<!--  Note: if a page's front matter contains "sitemap: false", it will not occur here or in sitemap.xml. -->

{% include base_path %}

A list of all the posts and pages found on the site. For you robots out there, there is an [XML version]({{ base_path }}/sitemap.xml) available for digesting as well.


<h2>Pages</h2>
{% for post in site.pages %}
  {% if post.sitemap != false %}

  {% include archive-single.html %}

  {% endif %}
{% endfor %}

<h2>Posts</h2>
{% for post in site.posts %}
  {% if post.sitemap != false %}

  {% include archive-single.html %}

  {% endif %}
{% endfor %}

{% capture written_label %}'None'{% endcapture %}

<!-- Collections include posts that are part of collections, as listed in config.yml. -->
{% for collection in site.collections %}
{% unless collection.output == false or collection.label == "posts" %}
  {% capture label %}{{ collection.label }}{% endcapture %}
  {% if label != written_label %}
  <h2>{{ label }}</h2>
  {% capture written_label %}{{ label }}{% endcapture %}
  {% endif %}
{% endunless %}
{% for post in collection.docs %}
  {% if post.sitemap != false %}

  {% unless collection.output == false or collection.label == "posts" %}
  {% include archive-single.html %}
  {% endunless %}

  {% endif %}
{% endfor %}
{% endfor %}
