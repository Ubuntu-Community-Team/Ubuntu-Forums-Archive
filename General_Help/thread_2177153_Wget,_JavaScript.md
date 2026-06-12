---
title: "Wget, JavaScript"
date: 2013-09-27
forum: General Help
---

### Post by twan2 on 2013-09-27
I am trying to download a couple of pages from this publicly available website:
[http://lt.morningstar.com/gay09rt8h3/fundquickrank/default.aspx](http://lt.morningstar.com/gay09rt8h3/fundquickrank/default.aspx)

As you can see it is a list of funds. Downloading the first page is easy, but I would like to do 2 things:
- first change the number of rows to 500 (as with the drop down box near the bottom of the list)
- download all available pages (like clicking the next button)

As these buttons are coded with JavaScript I have no clue how to do this, but if might be handy if i could tell wget to click this buttons for me. Is there a possibility to do such a thing?

---

### Post by sudodus on 2013-09-29
Welcome to the Ubuntu Forums :-)

I don't think wget will click buttons for you. It is a command line program. Maybe you can do it with ***xdotool*** in combination with a GUI browser, for example Firefox.

---

### Post by Lars Noodén on 2013-09-29
[wget](http://manpages.ubuntu.com/manpages/raring/en/man1/wget.1.html) will spider pages for you, but you have to be careful that you don't bog down the remote site with unecessary requests and that you don't harvest more than you need.  

See the following options in the wget manual page:

 --mirror
 --no-parent
 --wait=s

---

