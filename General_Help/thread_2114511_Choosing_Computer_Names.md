---
title: "Choosing Computer Names"
date: 2013-02-10
forum: General Help
---

### Post by jonesyp on 2013-02-10
Hi,

I am struggling in picking computer names. In the future I want to be able to network these together. I have a number of computers running Ubuntu, Fedora, openSUSE, Windows 7, and Windows Server 2012, and Windows XP.

I hear some versions of Windows are case sensitive with names and other not.

What is the general rules regarding upper and lower case and spaces in computer names.  

Also has anybody got any ideas for names?

Thanks

Peter Jones

---

### Post by TheFu on 2013-02-10
Computer name should never be case sensitive because DNS is not. I stay 100% lowercase to prevent issues from poorly written software.

DNS does not allow spaces or underscores, so you shouldn't use those either. Numbers, letters and dashes are allowed.
Having different names for Netbios vs virtual machines vs DNS is a terrible idea and only leads to confusion.

DNS has a limit on the total length of an entry - the FQDN - I think it is 64-chars, but don't quote me.  You can find the DNS RFC which specifics the limits with google.

So, when I'm naming computers, I try to stick with names that will mean something to insiders, but nothing to outsiders for the formal `**hostname**` result.  Then I'll use DNS aliases for any specific services provided - like www, mail, ns, dms, crm, ... you get the idea.

For the real computer names, I've seen and used many different groupings.
* car models
* stars
* planets
* superheros
* super-villains
* cities in {country} (helps learn them)
* Constellations
* Disney characters
* Movie characters (stay in a single movie or genre please)
* Greek/Roman gods
* Mexican foods (guacamole and fajita)
... you get the idea.

I prefer shorter names.  At home, I'm currently using star names. [https://en.wikipedia.org/wiki/List_of_proper_names_of_stars](https://en.wikipedia.org/wiki/List_of_proper_names_of_stars)

---

### Post by Marzata on 2013-02-11
Writers, volcanoes, etc.

---

### Post by CaptainMark on 2013-02-11
If you've made your network appropriately secure the obvious one is where (or what)the computers are,
ie. for small networks (like mine)
desktop
laptop
netbook
raspberrypi

or work areas for the office
accounting1
accounting2
reception
callcentre1
callcentre2
etc.

---

