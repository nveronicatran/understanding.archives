---
title: Meta-Archives
layout: default
---

<div class="info">
    <div class="key">
    <ul>
        <li>Key:</li>
        <li><i class="fa fa-file-text" aria-hidden="true"></i> PDF</li>
        <li><i class="fa fa-external-link-square" aria-hidden="true"></i> Website</li>
        <li><i class="fa fa-book" aria-hidden="true"></i> Book</li>
    </ul></div>

    <div class="about-link"><a href="{{ site.github.url }}/about">About</a></div>
</div>

<div class="blog-list-container" id="all-container">

          {% for post in site.posts %}
 <a href="{{ post.link }}">
            <div class="reading">
            <div class="icon">{{ post.type }}</div>
            <div class="title">{{ post.title }}</div>
            <div class="author">{{ post.author }}</div>
            <div class="year">{{ post.year }}</div>
                </div>
    </a>
          {% endfor %}
      </div>

      {% for tag in site.tags %}
        {% assign c = tag | first %}
        {% assign posts = tag | last %}
        <div class="blog-list-container hidden" id="{{ c }}-container">

            {% for post in posts %}
              {% if post.tags contains c %}
 <a href="{{ post.link }}">
            <div class="reading">
            <div class="icon">{{ post.type }}</div>
            <div class="title">{{ post.title }}</div>
            <div class="author">{{ post.author }}</div>
            <div class="year">{{ post.year }}</div>
                </div>
    </a>
              {% endif %}
            {% endfor %}

        </div>
      {% endfor %}


<script>

    function filter(tag) {
  setActivetag(tag);
  showContainer(tag);
}

function setActivetag(tag) {
  // loop through all items and remove active class
  var items = document.getElementsByClassName('blog-tags-item');
  for(var i=0; i < items.length; i++) {
    items[i].setAttribute('class', 'blog-tags-item');
  }

  // set the selected tag's item to active
  var item = document.getElementById(tag + '-item');
  if(item) {
    item.setAttribute('class', 'blog-tags-item active');
  }
}

function showContainer(tag) {
  // loop through all lists and hide them
  var lists = document.getElementsByClassName('blog-list-container');
  for(var i=0; i < lists.length; i++) {
    lists[i].setAttribute('class', 'blog-list-container hidden');
  }

  // remove the hidden class from the list corresponding to the selected tag
  var list = document.getElementById(tag + '-container');
  if(list) {
    list.setAttribute('class', 'blog-list-container');
  }
}


    </script>