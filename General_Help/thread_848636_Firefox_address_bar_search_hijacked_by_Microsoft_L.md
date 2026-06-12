---
title: "Firefox address bar search hijacked by Microsoft Live Search"
date: 2008-07-03
forum: General Help
---

### Post by fatski on 2008-07-03
Hi,

Wasn't sure where to post this and to be honest I don't even think it's a Ubuntu specific thing but I'm hoping I can get some help.

The problem is that whenever I type a search term into the Firefox (3.0) address bar, instead of taking me either to a google search results page or the I'm Feeling Lucky website I get presented with a Live Search results page. I've checked the keyword.url in about:config and it definitely points to Google.

A possibly related weirdness happened yesterday which might help some knowledgeable person diagnose the problem. For about 10 minutes (possibly while my internet connection was playing up) EVERY link I clicked took me to a Live Search results page for terms contained in the text of the link.

Anybody any ideas? I'm running hardy and connecting to the internet using wifi through a NETGEAR router.

Cheers

---

### Post by bubba_169 on 2008-07-03
Wierd... Maybe Microsoft have got fed up of being attacked by viruses and decided to write one of their own? :D

Sorry I've not a clue :lolflag:

EDIT: maybe a clue? Have you tried the drop down list next to the search bar?

---

### Post by fatski on 2008-07-03
Yep, it's set to google and if I use the search box I get a google results page. It's the address bar quick search that's all weirded up. For example, if I type ubuntuforums (without .org or anything) into the address bar, what should happen is that I automagically land at this forum by way of a google I'm Feeling Lucky search, what actually happens is I get a Live Search results page for ubuntuforums. Gah.

---

### Post by daleus on 2008-07-05
Your ISP has changed their url search provider.

If anyone uses opendns they see the same effect as their inurl bar search changes to a yahoo clone from opendns.

---

### Post by fatski on 2008-07-05
Ah, I see. The swine. Still in all other respects they're quite good, nice speeds and guaranteed no traffic throttling. Is there any way round it or is it something I just have to live with? I much prefer google.

Thanks for clearing it up for me.

---

### Post by eboni on 2008-07-13
omg ive been having this problem for a few days and wondering what its all about, thought it was just firefox 3.0 but 2.0 is doing it too. Is there anything i can do to change it bk.. i miss google.

---

### Post by fatski on 2008-07-14
I've still got it. It's not my ISP either, my flatmates PC (behind the same router) and this computer running windows both perform as they should when using the firefox address bar.

---

### Post by brad hart on 2008-07-15
> **eboni said:**
> omg ive been having this problem for a few days and wondering what its all about, thought it was just firefox 3.0 but 2.0 is doing it too. Is there anything i can do to change it bk.. i miss google.

thank god I am not the only one going crazy over this.  This is happening on my windows xp machine, but none of the others and it is only happening in firefox 2 and 3 too.  I can use my googe bar on the linux, vista, and  even my win 2k box I can also use it in every over browser on my main machine.  It didn't notice this happening until after I installed dotNetFx35setup last night.  I am getting ready to uninstall this and see if it works.  I hope this helps someone

---

### Post by brad hart on 2008-07-15
> **brad hart said:**
> thank god I am not the only one going crazy over this.  This is happening on my windows xp machine, but none of the others and it is only happening in firefox 2 and 3 too.  I can use my googe bar on the linux, vista, and  even my win 2k box I can also use it in every over browser on my main machine.  It didn't notice this happening until after I installed dotNetFx35setup last night.  I am getting ready to uninstall this and see if it works.  I hope this helps someone

Uninstalling dot net didn't help, but I found I can use my custom google search to work without any problems
[URL="http://bradstinyworld.com/network-search/"]
http://bradstinyworld.com/network-search/[/URL]

---

### Post by fatski on 2008-07-20
Bump

---

### Post by vancouverite on 2008-09-11
Have you tried deleting ~/.mozilla folder?

In terminal backup your bookmarks:
$ mv ~/.mozilla/firefox/[something**crazy].default/bookmarks.html ~/bookmarks_backup.html

Now remove the folder 
$ rm -r ~/.mozilla

When you restart Firefox it will recreate this folder.  Hope this works.

---

### Post by fatski on 2008-09-11
Strange as it sounds, I moved to a new flat, same ISP, same router, same set up in all other respects, and the problem just evaporated. Don't know if it was an update or some kind of magic but I'm happy all tyhe same.

---

