---
title: "Fonts are beautiful except for one particular setting in web pages"
date: 2008-05-07
forum: General Help
---

### Post by matthew on 2008-05-07
I am using Ubuntu 8.04, fully updated to today.

My fonts look beautiful. They look great in Gnome, in all my programs, in Open Office, Firefox, everywhere...except in one unique case.

When I browse a web page in Firefox (using 3 beta 5) or Epiphany and I come to a page that uses a css setting like this
```
h1, h2, h3, h4, h5, h6 {
  margin: 0;
  padding: 0;
  font-weight: normal;
  font-family: Helvetica, Arial, sans-serif;
}

h1 {
  font-size: 170%;
}

h2 {
  font-size: 160%;
  line-height: 130%;
}

h3 {
  font-size: 140%;
}

h4 {
  font-size: 130%;
}

h5 {
  font-size: 120%;
}

h6 {
  font-size: 110%;
}

```
then the font in question ends up not being antialiased at all, as in the attached photo, from my business web page. [The site]("http://derbyandwehttam.com/") (ignore the link if you don't want to see my business site) looks good in Opera. The site looks good in IE. The site looks good in Firefox and Epiphany on other computers.

This only happens when browsing a site that uses these fonts and which changes the font size using a percentage. I have Arial (and all the mstcorefonts) installed. I do not have Helvetica. I don't think that is the real issue, though.

I've reconfigured my fonts numerous times on this machine. I've tried different browsers (and this happens with BOTH Firefox and Epiphany). I'm out of ideas. Overall, this is trivial, because I can set either browser to use whatever fonts I choose, but I create websites and need/want to see them using the fonts that are chosen by the site designers (sometimes me). It is also bugging me because I don't the cause.

Anyone have any ideas??

---

### Post by Bastanteroma on 2008-05-08
For what it's worth, the fonts on your webpage look perfectly smooth to me on Hardy. The only configuring I've done was to install the microsoft fonts that are part of ubuntu-restricted-extras. Maybe try that? Or a fresh configuration?

---

### Post by MikeKnoop on 2008-05-08
I checked out your site as well, and the font in question is anti-aliased. I'm on 8.04, using default font settings and having installed the mstcorefont package.

-Mike

---

### Post by matthew on 2008-05-08
Thanks guys. I am certain this is a local problem with my computer and not the site (thankfully!).

It bugs me that I can't seem to figure out why. I've reconfigured my fonts in every way I can think of, both from the terminal and via the GUI. I've installed every font package I could find that seemed applicable.

There must be some hidden gecko (the engine that both Epiphany and Firefox use) setting somewhere that I have not found that somehow got adjusted.

Hmm... more searching.

---

