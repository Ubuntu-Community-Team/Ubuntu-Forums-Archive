---
title: "Weird font issue on certain website, not server side issue."
date: 2013-03-14
forum: General Help
---

### Post by zero2xiii on 2013-03-14
Hay all,

I have this strange occurrence that when I visit Hack A Day website (hackaday.com) on my computer I get garbage text.
(note I have never experienced this on another website, and only some times)


This happens on all my browsers:
Opera
Firefox
Chrome

The affected text alter between the body and the headers. Some time the body of the text, some time the headers, sometimes nothing is affected.
(see the attached image for an example of the body being affected).

I have emailed them and it is not a server side issue, and only I am experiencing this rather bizarre issue.

_*My question is:*_
How do I re-install my system's font. As this is presumably the thing causing issues.
Or any other advice in regards to fixing this.

Kind regards

---

### Post by schragge on 2013-03-14
The CSS on the site specifies ```
font-family: DroidSansRegular,Arial,Helvetica,Tahoma,sans serif;
```
Try ```
sudo apt-get install fonts-droid
```
But this won't remove the root cause that one of the fonts doesn't render correctly on your system. You can try *fc-match fontfamily* to see what substitutes you get for the fonts from the list above that you don't have installed, e.g.
```
fc-match Arial
fc-match 'sans serif'

``` and so on

---

### Post by zero2xiii on 2013-03-14
Hay,

I already have that font package installed. I removed and re-installed it.

After the re-install:
```
~/:~$ fc-match DroidSansRegular;fc-match Arial; fc-match Helvetica; fc-match Tahoma; fc-match sans serif
DejaVuSans.ttf: "DejaVu Sans" "Book"
Arial.ttf: "Arial" "Normal"
n019003l.pfb: "Nimbus Sans L" "Regular"
DejaVuSans.ttf: "DejaVu Sans" "Book"
```

What puzzles me is the fact that I can not find a pattern for when the strange characters are used....

:?

---

