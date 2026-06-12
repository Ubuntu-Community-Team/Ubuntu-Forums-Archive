---
title: "HTML desktop widgets"
date: 2014-07-07
forum: General Help
---

### Post by micwit2 on 2014-07-07
I want to be able to write a desktop widget as easy as possible. I read there is support for html5 widgets, but cant find a simple "hello World" tutorial to set one up. One of the reasons that I wanted to do this (there are a few things I wanted to do down the track as well) is to drop a web based cruise countdown in. So the cruise company give the following code:

```
<script type='text/javascript'>
(function() {document.write('<div id="cd62"></div>');
s62 = document.createElement('script');s62.type = "text/javascript";
s62.src = "http://services.pocruises.com.au/cdjs.aspx?t=countcam&c=reef&cruisecode=W429Q&id=cd62";
setTimeout("document.getElementById('cd62').appendChild(s62)", 1);})()
</script>
```

And I want to be able to drop this into a widget. Any ideas or good resources? Someone has to have set up a template or something for this purpose I would have thought?

---

