---
title: "MathML and Firefox?"
date: 2005-04-10
forum: General Help
---

### Post by dilerra on 2005-04-10
Hi everyone,

Have tried installing MathML-fonts on my system, but I must be doing something wrong, because all the pages containg MathML are looking really messed up. Firefox isn't complaining about fonts are being missed, but it still won't render them properly (or I've misconfigured something).

Has anyone had success with MathML and Firefox on Hoary Hedgehog?

Thanks in advance / Matthew

---

### Post by peter07 on 2005-07-29
[QUOTE=dilerra]Hi everyone,

Have tried installing MathML-fonts on my system, but I must be doing something wrong, because all the pages containg MathML are looking really messed up. Firefox isn't complaining about fonts are being missed, but it still won't render them properly (or I've misconfigured something).

Has anyone had success with MathML and Firefox on Hoary Hedgehog?

Thanks in advance / Matthew[/QUOTE]
 Check this site: [http://www.mozilla.org/projects/mathml/fonts/](http://www.mozilla.org/projects/mathml/fonts/)

I've tried latex-xft-fonts - only few symbols doesn't work. 

Now I'm testing Mathml and when I get some more info I will write here.

---

### Post by manobes on 2005-08-07
[QUOTE=dilerra]Hi everyone,

Have tried installing MathML-fonts on my system, but I must be doing something wrong, because all the pages containg MathML are looking really messed up. Firefox isn't complaining about fonts are being missed, but it still won't render them properly (or I've misconfigured something).

Has anyone had success with MathML and Firefox on Hoary Hedgehog?

Thanks in advance / Matthew[/QUOTE]

Hi, I had this problem too.  All the fonts were installed but the rendering was screwed.  I switched to mozilla rather than firefox, and it all works great.  The mathml torture test renders and everything.  I'm guessing firefox just doesn't support mathml.

---

### Post by superduper on 2005-11-05
:) 

It turns out that you shoud disable the pango option in /usr/bin/firefox as pointed out in [http://forums.fedoraforum.org/showthread.php?t=79480]("http://forums.fedoraforum.org/showthread.php?t=79480")
as follows: if any, comment out pango enable option, then insert in your /usr/bin/firefox file
```
 
MOZ_DISABLE_PANGO=1
export MOZ_DISABLE_PANGO 

```. Now, when you disable pango, you lose minus sign and few other symbos like pi and partial derivative sign as you can check on the [ MathML Torture Test page ]("http://www.mozilla.org/projects/mathml/demo/texvsmml.xhtml").

To get back the minus sign, I had to insert the following in about:config,
 ```
"font.mathfont-family.\u2212.base","Times"
```, as expounded in 
[http://golem.ph.utexas.edu/~distler/blog/archives/000652.html]("http://golem.ph.utexas.edu/~distler/blog/archives/000652.html").

Finally, to reclaim the other signs like pi, I had to resort to one of the two options explained in [Bug#307129:mozilla-firefox: characters missing in MathML rendering]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/5d6e729e5a3faea/2d3e5cbee35b81f7?lnk=st&q=firefox+mathml&rnum=3#2d3e5cbee35b81f7").

For me, I chose to edit the ".fonts.conf" file in my home directory and insert  
> 
<match target="pattern">
   <test name="family">
     <string>Symbol</string>
   </test>
   <edit name="family" mode="assign" binding="strong">
     <string>Standard Symbols L</string>
   </edit>
 </match>
 .

I could see mathml rendered correctly only after jumping through all these hoops:mad: ! What a shame. In Windows, all this hassle was unnecessary. To quote from [Installing MathML]("http://mcelrath.org/Notes/MathML"), > Getting MathML working on linux is TRULY a bitch!

---

