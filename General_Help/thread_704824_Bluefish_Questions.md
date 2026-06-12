---
title: "Bluefish Questions"
date: 2008-02-22
forum: General Help
---

### Post by JaggedOne on 2008-02-22
I have just started using bluefish to create HTML documents. I have three questions about it.

1. How do I customize what comes up by default with the quickstart button. I prefer transitional to strict HTML. It also adds way to many meta tags for my tastes. How do I change this?

2. How do I get preview in an external browser to work? I click on the preview button and nothing happens.

3. I have heard tell that there is some sort of built in HTML validation. Is this the same thing effectively as validating your code on W3.org? Also, how do I get bluefish to do it? I can't even find the validation button.

---

### Post by JaggedOne on 2008-02-23
Bump, can anyone help me?

---

### Post by JaggedOne on 2008-02-24
No one ever answers my questions anymore... :(

---

### Post by pointone on 2008-02-24
[http://bluefish.openoffice.nl/manual/](http://bluefish.openoffice.nl/manual/)

[http://bfwiki.tellefsen.net/](http://bfwiki.tellefsen.net/)

---

### Post by andrew.46 on 2008-02-25
Hi,

 I can see that you are feeling a little unloved :( Perhaps I can help with at least one of your questions:

> **JaggedOne said:**
> 
2. How do I get preview in an external browser to work? I click on the preview button and nothing happens.

If you look at Edit ===> Preferences ===> External Programs you will see the presets for external preview. Firefox will more than likely not be there and can be added as:

```
Label       Command   
Firefox    firefox "%s"
```

And then dragged with the mouse to the top of the list. This will make it the default to be opened by clicking on the 'View in Browser' button. Details at:

[http://bluefish.openoffice.nl/manual/ch07s08.html#external-browsers](http://bluefish.openoffice.nl/manual/ch07s08.html#external-browsers)

I don't personally use the 'Quickstart' button or the other checking, I have my own template for new pages and checking using the Web Developer Toolbar so cannot really advise with your other questions. except to point you to:

[http://bluefish.openoffice.nl/manual/bk01-toc.html](http://bluefish.openoffice.nl/manual/bk01-toc.html)

which will hopefully contain some useful tips.

                   Andrew

---

### Post by JaggedOne on 2008-02-25
> **andrew.46 said:**
> Hi,

 I can see that you are feeling a little unloved :( Perhaps I can help with at least one of your questions:



If you look at Edit ===> Preferences ===> External Programs you will see the presets for external preview. Firefox will more than likely not be there and can be added as:

```
Label       Command   
Firefox    firefox "%s"
```

And then dragged with the mouse to the top of the list. This will make it the default to be opened by clicking on the 'View in Browser' button. Details at:

[http://bluefish.openoffice.nl/manual/ch07s08.html#external-browsers](http://bluefish.openoffice.nl/manual/ch07s08.html#external-browsers)

I don't personally use the 'Quickstart' button or the other checking, I have my own template for new pages and checking using the Web Developer Toolbar so cannot really advise with your other questions. except to point you to:

[http://bluefish.openoffice.nl/manual/bk01-toc.html](http://bluefish.openoffice.nl/manual/bk01-toc.html)

which will hopefully contain some useful tips.

                   Andrew

Thanks for the help. Think you could tell me how to get the web developer toolbar and create a template? Those sound helpful.

---

### Post by andrew.46 on 2008-02-25
Hi,

 Glad my post was helpful:

> **JaggedOne said:**
> Thanks for the help. Think you could tell me how to get the web developer toolbar and create a template? Those sound helpful.

The web developer toolbar is a Firefox extension and can be downloaded at:

[https://addons.mozilla.org/en-US/firefox/addon/60](https://addons.mozilla.org/en-US/firefox/addon/60)

It would have to the most valuable learning tool for web makers that I have ever used. As for the template I have simply created a few and saved them as html files, nothing fancy or bluefish specific. A sample here:

[http://www.andrews-corner.org/template_2.html](http://www.andrews-corner.org/template_2.html)

 All the best,

   Andrew

   Andrew

---

