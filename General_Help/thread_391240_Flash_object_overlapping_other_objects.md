---
title: "Flash object overlapping other objects"
date: 2007-03-22
forum: General Help
---

### Post by GoodPanos on 2007-03-22
Hello!  I am a web developer and recently I began modifying a website for improvements and so forth.  The website has a flash movie playing on the front page.  It also has drop-down menus that are made up of div tags and CSS.  When they drop down they appear behind the flash movie instead of on top of it.  The Flash object overlaps the menu items.

This was also happening in Windows.  So I did some research and found out that I had to include the following parameter in the Flash object:
```
<param name="wmode" value="transparent" />
```
So I did and that took care of the problem in all the browsers Firefox, IE7.0, IE6.0, and Opera.  But for some reason that is not correcting the overlap issue in Ubuntu :( .  I haven't tried this in any other distro.

I know this is probably a question for Adobe, but we have a great community here and I'm hoping some one has a solution.

---

### Post by disturbedite on 2007-03-23
> **GoodPanos said:**
> I know this is probably a question for Adobe, but we have a great community here and I'm hoping some one has a solution.

not necessarily.  you should post which version of flash you're using both on the page and as a plugin.  it could be an ubuntu packaged flash plugin, so if that was the case, it wouldn't be adobe's fault, but it would be a problem with the ubuntu maintainer of that package.

i wish i could help you more, but someone else with more experience in this field will have to help you resolve this.

---

### Post by GoodPanos on 2007-03-23
> you should post which version of flash you're using both on the page and as a plugin I should have put that in my original post.

On the page it's 7.0 and I have 9.0 installed on Ubuntu.

---

### Post by DC@DR on 2007-05-05
I did google the web and found out that it's the issue of beta flash player version (9.0) for linux. I do hope they will fix it in the final release, adding together with full-screen mode feature :-)

---

### Post by ironmule on 2007-05-24
From the response I got from an adobe rep it has something to do with linux browsers not supporting wmode correctly. He didn't exactly give me much hope that a solution would be coming soon.

---

