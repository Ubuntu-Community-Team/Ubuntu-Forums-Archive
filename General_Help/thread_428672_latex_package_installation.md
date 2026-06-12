---
title: "latex package installation"
date: 2007-04-30
forum: General Help
---

### Post by ofweb on 2007-04-30
I am new to ubuntu and linux. i'm trying to set up latex, for me to write my reports in.
I've decided to use texlive and texmaker which i've installed for the repository and it works fine but i need to install a addon or package which is made by the university i'm studying at. The package comes as the source and a some .cls files. 
how do I install this package? it can be downloaded here [http://dirac.ruc.dk/imfufalatex/il3.zip](http://dirac.ruc.dk/imfufalatex/il3.zip)
I have look at [http://ubuntuforums.org/showthread.php?t=334047](http://ubuntuforums.org/showthread.php?t=334047) but it did not help a lot.

---

### Post by venik212 on 2007-05-01
Did you have to do anything other than install TexLive from Adept/Synaptic?  When I did that it did not work-- I get an empty output file from Lyx or from Kile.

---

### Post by ofweb on 2007-05-01
no, I just installed texlive and texmaker from synaptic and it worked

---

### Post by venik212 on 2007-05-02
I had to run texconfig and texhash, which started the pdf Latex process going, but still did not produce a correct pdf (no figures or references).

---

