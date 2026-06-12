---
title: "JSON editor recommendation"
date: 2017-11-13
forum: General Help
---

### Post by kazakore on 2017-11-13
Can somebody please suggest me a simple but useful JSON editor. I had hoped Codeblock would have support as it's what I'd used for basic programming before and still had installed. I'm perfectly happy with viewing through my browser (Waterfox/Firefox) as this formats it with the expandable columns etc but I'd like to be able to edit it in a program with a similar view, one must have but basic feature is to be able to search and replace for text within a highlights (non-expanded) section of the file/code.

---

### Post by kazakore on 2017-11-13
OK I can only use it while I have access to the internet but this is the best I've found and will do me for now....

[http://www.jsoneditoronline.org/](http://www.jsoneditoronline.org/)

---

### Post by dragonfly41 on 2017-11-13
Here is one example of a lengthy custom command which I use to colour json output from ansible ..

```
/etc/ansible/inventory/gce.py --list |  python -m json.tool | pygmentize -l json | aha
```

[COLOR=#333333][FONT=Roboto]so you need .. python, json.tool, pygmentize and aha to be installed.[/FONT][/COLOR]

---

### Post by kazakore on 2017-11-21
Just had a recommendation of Sublime Text editor, by a friend kicked off from a separate conversation. Yet to actually try it but definitely looks promising :)

[http://tipsonubuntu.com/2017/05/30/install-sublime-text-3-ubuntu-16-04-official-way/](http://tipsonubuntu.com/2017/05/30/install-sublime-text-3-ubuntu-16-04-official-way/)

---

### Post by pc-linux on 2018-08-19
> **kazakore said:**
> Just had a recommendation of Sublime Text editor, by a friend kicked off from a separate conversation. Yet to actually try it but definitely looks promising :)

[http://tipsonubuntu.com/2017/05/30/install-sublime-text-3-ubuntu-16-04-official-way/](http://tipsonubuntu.com/2017/05/30/install-sublime-text-3-ubuntu-16-04-official-way/)

You don't need proprietary software.

just

apt-get install geany-common

apt-get install geany

apt-get install geany-plugins

Geany is the swiss army knife of free software editor normally I use it to write book in latex.

Here are some hints
[https://wiki.geany.org/config/json]("https://wiki.geany.org/config/json")
[https://subhadipsblog.wordpress.com/2017/09/23/opening-large-json-files-with-geany/]("https://subhadipsblog.wordpress.com/2017/09/23/opening-large-json-files-with-geany/")

Hope this help to avoid use of non free software in GNU/Linux

---

### Post by oldos2er on 2018-08-19
Old thread closed.

---

