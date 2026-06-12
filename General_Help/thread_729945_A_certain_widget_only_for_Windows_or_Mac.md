---
title: "A certain widget: only for Windows or Mac?"
date: 2008-03-20
forum: General Help
---

### Post by Th3Professor on 2008-03-20
I'd like to install/run a certain widget, though it says it is only available for Microsoft Windows or Mac OS X.

The widget requires installing the program "Yahoo! Widgets" ("Yahoo! Widgets Engine").

It's a custom widget created for use with a city mass transit system (such as the schedule for the city bus), so unfortunately I cannot just use any other random widget.

Is there a way to get it working, or to get the yahoo win/mac-only program working?

(Trying to avoid resorting to WINE.)

Thank you.

---

### Post by scramasax on 2008-03-20
> **Th3Professor said:**
> The widget requires installing the program "Yahoo! Widgets" ("Yahoo! Widgets Engine").

IIRC, these are written in XML, CSS, and JavaScript.  Apple's version, which was based on it, is much the same except it uses XHTML (effectively a webpage) instead of whatever version of XML Yahoo uses.  MS now offers something similar, and so does Opera.  It's logical enough thing to tack onto a browser -- these things are basically written in web languages.

What I'm thinking is that, AFAIK, there's a version of Opera in the repositories.   Is there an Opera widget for transport the city in question?

[http://widgets.opera.com/](http://widgets.opera.com/)

---

### Post by Th3Professor on 2008-03-20
> **scramasax said:**
> IIRC, these are written in XML, CSS, and JavaScript.  Apple's version, which was based on it, is much the same except it uses XHTML (effectively a webpage) instead of whatever version of XML Yahoo uses.  MS now offers something similar, and so does Opera.  It's logical enough thing to tack onto a browser -- these things are basically written in web languages.

What I'm thinking is that, AFAIK, there's a version of Opera in the repositories.   Is there an Opera widget for transport the city in question?

[http://widgets.opera.com/](http://widgets.opera.com/)

Thank you for the quick reply... it sounds like there might be a work around for getting that widget working.

I went ahead and tried WINE but the yahoo widget program didn't work with it.

I checked the package manager (multiple repos) for the opera browser but it didn't come up in the search list. Very odd! I've used Opera before and was very happy with it - and I remember it having gobs of widgets.

This particular widget I'm talking about is supposed to run separate from a browser. I don't know if Opera would recognize a "yahoo widget engine" widget... ?

I took a look at the actual widget, it is a data/binary... there's some legible text in the file... including "<?xml version="1.0">. Partway through the file is mention of Adobe. I'm not really familiar with XML but I wouldn't mind taking somewhat of an 'unorthodox' approach with it if there's a way I can just take the widget file and get it to work through some manual steps.

---

