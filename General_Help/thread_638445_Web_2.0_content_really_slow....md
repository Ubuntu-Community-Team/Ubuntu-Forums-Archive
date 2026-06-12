---
title: "Web 2.0 content really slow..."
date: 2007-12-12
forum: General Help
---

### Post by akudewan on 2007-12-12
Over a period of time I noticed my web browser (firefox) getting slower and slower. There came a point when using it became practically impossible. I considered shifting over to Opera, but even that didn't make much of a difference.

Then I noticed that if I close my *iGoogle* homepage tab, the browsers(both firefox and opera) speed up dramatically.

Next, I noticed that almost all Web 2.0 content (like GMail, Facebook) is slowing down the browsers. Heck, there's almost a one second lag when I try to scroll a page in GMail...

I tried renaming my ~/.mozilla directory, but that didn't make any difference. I also tried running GMail with some *ui=1* option in the address. This did increase speed, but I like the features that the newer ui provides...

When I run the same in windows(with firefox again), these sites are as fast as any other website. I don't understand why they're so slow in Linux. The horrible virus infected PCs in my college, with a slower internet connection are able to run GMail faster...

(I also tried removing unnecessary processes using BUM (boot-up manager), that just ended up making linux faster, as a whole, with no effect on the browsing).

My system specs:
[LIST]
[*]Pentium 4 -  1.6GHz
[*]376MB RAM
[*]666 MB Swap
[*]128kbps internet connection
[*]Kubuntu Gutsy
[*]Kernel 2.6.22-14-generic
[*]Firefox 2.0.0.11
[/LIST]

Has anyone experienced anything similar. Is there any way to solve this problem ??

---

### Post by hendeca on 2007-12-13
I think I'm having a similar problem. My Firefox performance in Linux is pretty bad in general, let alone with more complex sites, compared to Windows.

---

### Post by akudewan on 2007-12-17
I installed SwiftFox (version 3.0b2pre), and GMail, (along with everything else) has sped up considerably. Unfortunately, some of my extensions don't work. But I can live with that...

I had tried SwiftFox version 2.0.0.11 earlier, but that did not make any difference with GMail. I'm thinking the 3.0 release had some code changes that have made it faster ?

@hendeca: I recommend you try out [SwiftFox]("http://getswiftfox.com/download.htm"). There's a repository available that can be added to /etc/apt/sources.list

---

### Post by akudewan on 2007-12-20
It seems there are, indeed many bug fixes in Firefox 3. Over 300 memory leaks have been fixed!

There's also an interesting article from codinghorror about JavaScript performance in web browsers: [http://www.codinghorror.com/blog/archives/001023.html](http://www.codinghorror.com/blog/archives/001023.html)

I'm really looking forward to the new firefox release :)

---

