# Stencil

[![Build Status](https://travis-ci.org/stencilproject/Stencil.svg?branch=master)](https://travis-ci.org/stencilproject/Stencil)

Stencil is a simple and powerful template language for Swift. It provides a
syntax similar to Django and Mustache. If you're familiar with these, you will
feel right at home with Stencil.

## Example

```html+django
Hello Arthur
Your beard trimmer will arrive on Nov 19, 2020.
Well, on Nov 19, 2020 because of a Martian attack.
```

```html+django
{% for item in items %}
  {{ item }}
{% endfor %}
```

```html+django
{{ variable|uppercase }}

{{ array|join:"-"|capitalized }}
```

template.stencil
```html+django
{# My comment is completely hidden #}
There are {{ articles.count }} articles.

<ul>
  {% for article in articles %}
    <li>{{ article.title }} by {{ article.author }}</li>
  {% endfor %}
</ul>
```

Renderer.swift
```swift
import Stencil

struct Article {
  let title: String
  let author: String
}

let context = [
  "articles": [
    Article(title: "Template Engine for Swift", author: "Sandy Akbar"),
    Article(title: "Automate Everything", author: "Sandy Akbar"),
  ]
]

let environment = Environment(loader: FileSystemLoader(path: "template.stencil"))
try environment.renderTemplate(name: "output.html", context: context)
```
output.html
```html+django
There are 2 articles.

<ul>
    <li>Template Engine for Swift by Sandy Akbar</li>
    <li>Automate Everything by Sandy Akbar</li>
</ul>
```


## Philosophy

Stencil follows the same philosophy of Django:

> If you have a background in programming, or if you’re used to languages which
> mix programming code directly into HTML, you’ll want to bear in mind that the
> Django template system is not simply Python embedded into HTML. This is by
> design: the template system is meant to express presentation, not program
> logic.

## The User Guide

Resources for Stencil template authors to write Stencil templates:

- [Language overview](http://stencil.fuller.li/en/latest/templates.html)
- [Built-in template tags and filters](http://stencil.fuller.li/en/latest/builtins.html)

Resources to help you integrate Stencil into a Swift project:

- [Installation](http://stencil.fuller.li/en/latest/installation.html)
- [Getting Started](http://stencil.fuller.li/en/latest/getting-started.html)
- [API Reference](http://stencil.fuller.li/en/latest/api.html)
- [Custom Template Tags and Filters](http://stencil.fuller.li/en/latest/custom-template-tags-and-filters.html)

## Projects that use Stencil

[Sourcery](https://github.com/krzysztofzablocki/Sourcery),
[SwiftGen](https://github.com/SwiftGen/SwiftGen),
[Kitura](https://github.com/IBM-Swift/Kitura),
[Weaver](https://github.com/scribd/Weaver),
[Genesis](https://github.com/yonaskolb/Genesis)

## License

Stencil is licensed under the BSD license. See [LICENSE](LICENSE) for more
info.
