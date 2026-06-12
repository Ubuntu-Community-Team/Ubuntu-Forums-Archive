---
title: "Libreoffice: modern presentation with HTML5 and JavaScript"
date: 2018-10-08
forum: General Help
---

### Post by erotavlas on 2018-10-08
Hi,

 I'm using latest LibreOffice v.6.1.2 to prepare "classical" presentation. Some slides have big tables  that do not find on them. I cannot use small font since the tables become  unreadable. I tried to convert the presentation into HTML format and the readability  is increased a lot.

 So after some searches on the Web, I'm  starting to think that "modern" presentation made of HTML5 and  JavaScript are more suited than classical plain .odp presentation.

 Then,  I found this big collection of modern HTML5 and JavaScript framework.
Does libreoffice provide something similar? If not, do you suggest one  of the listed framework?
I analysed in detail:[URL="https://github.com/jmpressjs/jmpress.js"]
[/URL]
[LIST]
[*][impress.js]("https://github.com/jmpressjs/jmpress.js") 
[*][reveal.js]("https://github.com/hakimel/reveal.js") 
[*][shower]("https://github.com/shower/shower") 
[/LIST]
 The latter seems the simplest and best option. Do you have any suggestion?
 Thank you

---

### Post by dragonfly41 on 2018-10-08
I am building presentations right now using reveal.js and I am a fan of this framework.

You might also look at pandoc which allows reveal.js or beamer presentations to be created from markdown.

If you are using big tables also explore Rmarkdown which can also be linked to shinyapps (RStudio) presentations.

i use Atom as my content editor and Atom Markdown Preview Enhanced plugin (plus others) allows presentations to be compiled from markdown slides.

---

### Post by erotavlas on 2018-10-09
Thank you for your fast reply.
I read many information about your suggestion. In your opinion, what is the most flexible way to write presentation in order to convert it to other format (PDF and HTML5)?
Do you think that the best source is markdown or Rmarkdown?
If I have some materials in latex, odp and odt format, what is the fastest way to obtain an HTML5 document? Pandoc?
Thank you

---

### Post by dragonfly41 on 2018-10-09
I don't have a handle yet on the size and scope of your problem/goal.

How many legacy presentations created to date to convert to HTML (review.js)?

What mix of content (text or mathematical expressions)?

Static or interactive presentations with user participation (requiring scripting)?

"Big tables" or graphical visualisation of data? See D3js plugin for Reveal.js for example.

Will there be many presentations ahead, or is this a one off exercise for a thesis?

So back to you. What is the scope and scale of your ambition?

> what is the most flexible way to write presentation in order to convert it to other format (PDF and HTML5)?

Within LibreOffice legacy presentations can be exported to HTML.

[https://help.libreoffice.org/Impress/Saving_a_Presentation_in_HTML_Format](https://help.libreoffice.org/Impress/Saving_a_Presentation_in_HTML_Format)

I am biased since I am integrating a toolchain which pipes content into layout engines for presentation and printing.
If flexibility and modularity (rather than ease of learning) is one goal then I would start with Atom and populate this with Atom community packages. On the other hand you don't need Atom framework if you don't have a large number of presentations to compose/manage ahead.

If you choose to experiment with Atom (quite a learning curve) I can dump here a list of packages I have installed for my purposes. I just run the command ```
apm list
```

I am also using free Heroku account to push presentation apps from local IDE.

Or you can experiment with [http://slides.com](http://slides.com)  (created by the creator of reveal.js).

> Do you think that the best source is markdown or Rmarkdown?

If you are presenting scientific content with illustrations then I would use Rmarkdown since you can link to shinyapps presentations through embedded iframe in reveal.js slide. However you can mix the content of each slide (section) to suit your purposes.

In Reveal.js I import content which has been pre-processed in Atom framework through a toolchain. Again in Reveal.js there is a spread of plugins which can be leveraged.

> If I have some materials in latex, odp and odt format, what is the fastest way to obtain an HTML5 document? Pandoc?

What context mix? I would start by looking at pandoc using just one line bash scripts but if you have legacy content you might embed LateX in slides.

[https://pandoc.org/](https://pandoc.org/)

---

### Post by erotavlas on 2018-10-09
> I don't have a handle yet on the size and scope of your problem/goal.

How many legacy presentations created to date to convert to HTML (review.js).

What mix of content (text or mathematical expressions)?

Static or interactive presentations with user participation (requiring scripting)?

"Big tables" or graphical visualisation of data? See D3js plugin for Reveal.js for example.

Will there be many presentations ahead, or is this a one off exercise for a thesis?

So back to you. What is the scope and scale of your ambition?


At the moment I would like to understand what is the best way for both legacy presentation and modern one.
The legacy classical presentations are mainly in odp format without mathematical expressions, but with a lot of big tables (libreoffice writer or calc tables) that do not fit in one slide. The other are in latex with a lot of mathematical expressions.
They are static presentation without or almost without any transitions and scripts.
I wrote some interesting (I think) presentations and I would like to publish them on the Web.

> 
Within LibreOffice legacy presentations can be exported to HTML.

[https://help.libreoffice.org/Impress...in_HTML_Format](https://help.libreoffice.org/Impress...in_HTML_Format)

Ok, I know this way.

> 
I am biased since I am integrating a toolchain which pipes content into layout engines for presentation and printing.
If flexibility and modularity (rather than ease of learning) is a criteria then I would start with Atom and populate this with community packages. On the other hand you don't need Atom if you don't have a large number of presentations to compose/manage ahead.

If you choose to experiment with Atom (quite a learning curve) I can dump here a list of packages I have installed for my purposes.


Thank you for the offer. No, this is not my job. I just want to publish some useful information on the Web in the best format (HTML5) for all platforms (PC and mobile).
At the moment I do not have enough time to learn something not simple that I will use only sometimes.

> 
What context mix? I would look at pandoc using just bash script but if you have legacy content you might embed LateX in slides.

[https://pandoc.org/](https://pandoc.org/)

I have several works wrote on different formats with the same requirements as before. Do you suggest to embed slides directly into HTML5?

---

### Post by dragonfly41 on 2018-10-09
> [COLOR=#000000][INDENT]Do you suggest to embed slides directly into HTML5?[/INDENT]
[/COLOR][COLOR=#000000]
[/COLOR]That is one quick way of getting started if you have assets already prepared.

Here is an example of embedding an iframe in slide:
```

<[COLOR=#22863A]section[/COLOR]>
  <[COLOR=#22863A]img[/COLOR] [COLOR=#6F42C1]data-src[/COLOR]=[COLOR=#032F62]"image.png"[/COLOR]>
  <[COLOR=#22863A]iframe[/COLOR] [COLOR=#6F42C1]data-src[/COLOR]=[COLOR=#032F62]"http://slides.com"[/COLOR]></[COLOR=#22863A]iframe[/COLOR]>
  <[COLOR=#22863A]video[/COLOR]>
    <[COLOR=#22863A]source[/COLOR] [COLOR=#6F42C1]data-src[/COLOR]=[COLOR=#032F62]"video.webm"[/COLOR] [COLOR=#6F42C1]type[/COLOR]=[COLOR=#032F62]"video/webm"[/COLOR] />
    <[COLOR=#22863A]source[/COLOR] [COLOR=#6F42C1]data-src[/COLOR]=[COLOR=#032F62]"video.mp4"[/COLOR] [COLOR=#6F42C1]type[/COLOR]=[COLOR=#032F62]"video/mp4"[/COLOR] />
  </[COLOR=#22863A]video[/COLOR]>
</[COLOR=#22863A]section[/COLOR]>

```

You just need to ensure that you have the correct plugins installed.

Play around in [http://slides.com](http://slides.com) which uses reveal.js.

---

### Post by erotavlas on 2018-10-09
> **dragonfly41 said:**
> [COLOR=#000000]
[/COLOR]That is one quick way of getting started if you have assets already prepared.

Here is an example of embedding an iframe in slide:
```

<[COLOR=#22863A]section[/COLOR]>
  <[COLOR=#22863A]img[/COLOR] [COLOR=#6F42C1]data-src[/COLOR]=[COLOR=#032F62]"image.png"[/COLOR]>
  <[COLOR=#22863A]iframe[/COLOR] [COLOR=#6F42C1]data-src[/COLOR]=[COLOR=#032F62]"http://slides.com"[/COLOR]></[COLOR=#22863A]iframe[/COLOR]>
  <[COLOR=#22863A]video[/COLOR]>
    <[COLOR=#22863A]source[/COLOR] [COLOR=#6F42C1]data-src[/COLOR]=[COLOR=#032F62]"video.webm"[/COLOR] [COLOR=#6F42C1]type[/COLOR]=[COLOR=#032F62]"video/webm"[/COLOR] />
    <[COLOR=#22863A]source[/COLOR] [COLOR=#6F42C1]data-src[/COLOR]=[COLOR=#032F62]"video.mp4"[/COLOR] [COLOR=#6F42C1]type[/COLOR]=[COLOR=#032F62]"video/mp4"[/COLOR] />
  </[COLOR=#22863A]video[/COLOR]>
</[COLOR=#22863A]section[/COLOR]>

```

You just need to ensure that you have the correct plugins installed.

Play around in [http://slides.com](http://slides.com) which uses reveal.js.

Ok, thank you. Is slides.com the paid version of reveal.js? Do you work for it?

---

### Post by dragonfly41 on 2018-10-09
> [COLOR=#000000]Is slides.com the paid version of reveal.js? Do you work for it?[/COLOR]

This is indeed the "paid version" although you can play with the slides editor if you don't mind your first experiment being public.

I do not work for slides.com.  As a solo developer I simply choose what technologies to experiment with.
I am working on applying the community version to a project I am developing but I only suggested slides.com when you wrote ...

> [COLOR=#000000]At the moment I do not have enough time to learn something not simple that I will use only sometimes.[/COLOR]

---

### Post by erotavlas on 2018-10-10
Thank you for all your help.

---

### Post by dragonfly41 on 2018-10-10
Just curious. To inform us, and to avoid guesswork, what route did you opt for?

---

### Post by erotavlas on 2018-10-11
I will use pandoc and libreoffice for classic presentation and material.
For new presentation, I'm still evaluating reveal, impress and shower.

---

### Post by erotavlas on 2018-10-21
I found [this plugin]("http://writer2latex.sourceforge.net/") for libreoffice that export to HTML very well. In particular, in the [URL="http://writer2latex.sourceforge.net/index7.html"]roadmap there is full support to HTML5.

[/URL]

---

