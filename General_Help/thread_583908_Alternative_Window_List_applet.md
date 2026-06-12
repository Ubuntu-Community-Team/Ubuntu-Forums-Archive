---
title: "Alternative Window List applet?"
date: 2007-10-20
forum: General Help
---

### Post by lightstream on 2007-10-20
I like to have my Window List in a wide vertical panel on the left-hand side of the screen. I prefer that because it means I usually have many apps open all at once, and this way I can easily read the titles of each one at a glance. 

This image should make it clear what I mean:

[IMG]http://www.kuxas.com/windowlist.png[/IMG]

So, having upgraded to Gutsy, it's no longer possible to adjust the size of the Window List, and it will only ever take up the top few hundred pixels of my vertical bar. When I have more than seven applications open at once, it starts showing two vertical lists adjacent to each other, leaving the majority of the space empty and defeating the whole purpose of this arrangement. 

So are there any alternative applets that will let me use up the whole of a vertical panel like this? Or is there **any way to install the older Feisty version of Window List**?

(The Gnome Window Selector is unfortunately not what I need at all.)

If there isn't, I'm not sure what to do. Being able to easily view all open windows is essential to my productivity, and I would rather not have to go back to Feisty for something as apparently simple as this!

---

### Post by lightstream on 2007-10-21
Well ok, the Gnome Window Selector isn't too bad actually - it does show all the open apps nice and clearly, ok it requires an extra click but I think I can cope with that little extra workload!

If anyone does know of any other window list applets I'd like to hear about them - or indeed whether or not it's possible to run the Feisty version of Window List somehow.

Thanks ..

---

### Post by MegaSvensk on 2007-10-21
I like new window list. The old one was one of my least favorite things about Ubuntu 7.04. It was really annoying when the buttons changed size when you switched tabs in Firefox.

And I've got to say that I see more text in the window list button than what is visible in your mock-up. And how hard is it really to put your cursor on a button and read the little pop-up?

---

### Post by lightstream on 2007-10-21
I know that a lot of people didn't like the way the button would take up more room if there were not many apps open, or even change size when switching tabs in Firefox. But if you had your window list at the side like in my screenshot those problems didn't really exist. 

I'm not complaining about the window list, I realise it works better now for 90% or more of users, it's just no longer any good for me!

Surely there must be some way I can just install the Feisty version, I can't imagine there would be a reason it wouldn't work with Gutsy?

---

### Post by tolomea on 2007-10-23
I'm also using a side window list for the same reasons, along with the problem you are having I have the additional problem that it often can't decide if it wants to be in 1 column or two and sits there flicking back and forward between the two.

---

### Post by tolomea on 2007-10-23
incidentally the flicking behavior seems to be mostly related to focus (I have sawfish with focus on enter-only

---

### Post by beatnick on 2007-10-26
I had the same annoyance.

To workaround i've installed the xfce4-panel package.

I start it using the session manager of gnome (System->Prefs.->Sessions)

I've added just the task list to the panel.
My settings for the panel are : fixed position (left-middle), auto-hide, size=128. And for the task list : min width = 350, never group windows.

Here's a screenshot :

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=47944&stc=1&d=1193440619[/IMG]

Beatnick

---

### Post by lightstream on 2007-10-27
> **tolomea said:**
> I'm also using a side window list for the same reasons, along with the problem you are having I have the additional problem that it often can't decide if it wants to be in 1 column or two and sits there flicking back and forward between the two.
Yes I also got this flickering between 1 & two columns, and when it happened, it was hard to switch applications, as the Window List doesn't seem to register clicks very well when it's flickering. This is obviously a bug, I haven't checked if it's been reported yet, I guess I should do and report it if not.

---

### Post by lightstream on 2007-10-27
> **beatnick said:**
> To workaround i've installed the xfce4-panel package.
Thanks for the tip beatnick, it looks like this xfce4-panel thing might even be better than the Feisty Window List! Gonna give it a try...

---

### Post by tolomea on 2007-10-29
> **lightstream said:**
> Thanks for the tip beatnick, it looks like this xfce4-panel thing might even be better than the Feisty Window List! Gonna give it a try...

it certainly gets the job done which is more than can be said for the default panel

---

### Post by kerunt on 2008-02-28
I was having the exact same problems as described in this thread, and found that the xfce4-panel package suggested above solved them all! Works beautifully! Thanks!

---

