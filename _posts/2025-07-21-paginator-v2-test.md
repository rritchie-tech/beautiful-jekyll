---
layout: default
---
<!-- Rick Ritchie's Paginator Test -->
<style>
  ul.pager { text-align: center; list-style: none; }
  ul.pager li {display: inline;border: 1px solid black; padding: 10px; margin: 5px;}
</style>

<div class="home">

  <h1 class="page-heading">Posts</h1>
  
  {{ content }}

  <ul class="post-list">
    <!-- 
        Here is the main paginator logic called.
        All calls to site.posts should be replaced by paginator.posts 
    -->
    {% for post in paginator.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
        </h2>
      </li>
    {% endfor %}
  </ul>
  
  <!-- 
    Showing buttons to move to the next and to the previous list of posts (pager buttons).
  -->
  {% if paginator.total_pages > 1 %}
  <ul class="pager">
      {% if paginator.previous_page %}
      <li class="previous">
          <a href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&larr; Newer Posts</a>
      </li>
      {% endif %}
      {% if paginator.next_page %}
      <li class="next">
          <a href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">Older Posts &rarr;</a>
      </li>
      {% endif %}
  </ul>
  {% endif %}

  <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | relative_url }}">via RSS</a></p>

</div>