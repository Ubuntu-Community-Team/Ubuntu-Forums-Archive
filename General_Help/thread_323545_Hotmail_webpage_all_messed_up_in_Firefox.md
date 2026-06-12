---
title: "Hotmail webpage all messed up in Firefox"
date: 2006-12-22
forum: General Help
---

### Post by dannyboy79 on 2006-12-22
I was wondering why when I go to Hotmail within Firefox, it's all messed up?? Like it's missing pictures and whatnot. I don't know if this is because java isn't working or why but I do have java installed. Can anyone help me?? This website works fine in opera when I am in xubuntu on my laptop. maybe I should try firefox 3.0 if I can find it. i heard it's out already somewhere. I believe I am running firefox 2.0. but I'll have to double check once my putty session is done running nmap on a ip address that is trying to break into my ssh server. please help.

no I guess I don't have 2.0, according to sudo aptitude show firefox:
Automatically installed: no
Version: 1.5.dfsg+1.5.0.8-0ubuntu0.6.06.

so, any help would be appreciated.

---

### Post by raul_ on 2006-12-22
I think Firefox 2.0 is only available in Edgy's repos. You can always try installing it  manually. Anywayz, the hotmail page works fine here

---

### Post by matchstich on 2006-12-22
i use hotmail. it looks a lot different in firefox but it stll works.   i get double icons for everything.  well, not icons, they don't show, it just say delete twice, and so on.

also, i did a manual install of ff 2.0.0.1, but  my system still shows 1.5.0.9. was told it will stay that way till the newer version of firefox gets added to the repositories.
i am a newbie at ubuntu
thanks

---

### Post by xopher on 2006-12-22
> also, i did a manual install of ff 2.0.0.1, but my system still shows 1.5.0.9.

dpkg will still show the version of the deb installed, which in your case is 1.5. Programs you've installed from tarballs aren't accounted for by dpkg or apt, which makes it harder to uninstall, if it didnt provide an uninstaller.

I'm not sure, but check out dapper backports, firefox 2.0 might be available there too, which would make things, well, at least easier to keep up to date ;)

No idea why the page wouldn't look right in 1.5 though, it should. Maybe it was some setting or some extension you used in 1.5?

---

### Post by PurplePenguin on 2006-12-22
Hotmail works perfectly for me under Firefox 2 / Swiftfox 2.  No double icons or anything like that.  In fact, I just tried Windows Live Mail (you'll see a link to it from within Hotmail) - it makes Hotmail look more like an email client like Outlook Express or Thunderbird - and it works fine, too.

I'm running Firefox 2 with AdBlock Plus, flash 9 and java installed (just in case that makes some kind of difference).

EDIT: Here's a screenshot... I was going to go back to regular old Hotmail and take a screenshot to show that all is normal, but you get the idea. :)

---

### Post by dannyboy79 on 2006-12-22
> **PurplePenguin said:**
> Hotmail works perfectly for me under Firefox 2 / Swiftfox 2.  No double icons or anything like that.  In fact, I just tried Windows Live Mail (you'll see a link to it from within Hotmail) - it makes Hotmail look more like an email client like Outlook Express or Thunderbird - and it works fine, too.

I'm running Firefox 2 with AdBlock Plus, flash 9 and java installed (just in case that makes some kind of difference).

EDIT: Here's a screenshot... I was going to go back to regular old Hotmail and take a screenshot to show that all is normal, but you get the idea. :)

which java did you install, did you use automatix? i think that's how I installed java. do you know if hotmail main page uses flash, is that why maybe? well that wouldn't maek sence either because I installed flash using automatix also??? so all you guys are saying that your hotmail page is fine? except for that one guy, i think mine is like his, i don't have icons, just the words are there for like delete, send, etc etc. so what would this have to do with? does hotmail's website use java to render it's page? how do I find out what extensions I have installed? is there maybe anything in about:config that would tell me why this is screwed up? anymore help would be appreciated since no one really has attemped to help yet although I do appreciate you guys telling me how your systems are working though as it kind of helps me figure out what the differences are between your setup and mine. any troubleshooting tips would be appreciated. thanks

---

### Post by PurplePenguin on 2006-12-22
I don't know how much help I can be, since I'm not sure what could be making your browser act like this with Hotmail.  

Here are a couple ideas, though, although I'm not sure how relevant they might be.  First, do you have java and javascript turned on in Firefox?  (Edit -> Preferences -> Content - are both boxes checked?).  Maybe that could be related to the problem... not sure.  What about the other check box right above it, Load Images Automatically?  If that's turned off, you won't see any buttons, since I think the buttons are images.

To find out which extensions you're using, you can go to Tools -> Add-Ons, although I don't see anything there that might have anything to do with the problem you're having.

I don't use Hotmail that often, but I did use it when I had older versions of Firefox... it's always worked fine for me, as far as I know.

I think that I installed java the old fashioned way (that is, the first day I installed Ubuntu, I went to one of those beginners' how-to's in order to get multimedia and everything running).  I didn't install Flash with automatix, I just went to the flash site, downloaded one of the two available packages (which was just a .so file and a readme, IIRC), and copied the .so to my mozilla plugins folder.  I don't know if this is how most people do it, but that's what I did and it works perfectly. :)

I'm no good with about:config, so I'll leave that to somebody else.

If I think of anything else that might make it work for me, but not for you, I'll let you know.  Good luck!

---

### Post by dannyboy79 on 2006-12-22
thank you so much. i know from memory i have the 2 boxes checked for java but as far as the images being loaded that I am not sure about. hopefully it's as easy as that. I also have that script thingy installed, where it won't allow scripts to be run unless I allow the site to use them. I know that some sites that use flash, if I don't temp allow the site to use scripts, the site looks all messed up but I made it so this script killer thingy or whatever always allows hotmail to run scripts so that shouldn't be it. I think I installed 2.0 manually also but not sure, i'll look into that and maybe somehting from 1.5 is screwing up 2.0? it wouldn't make sence though that hotmail is the only affected site if that were the case. Thanks again for your input, I really appreciate it. i just started on linux about 9 months ago, i chose ubuntu as my first distro and have stuck with it. the main reason is the great support I get here in this forum, i mean it's supurb!!! thanks again. throw anymore ideas you may have out as I don't mind suggestions.

---

### Post by artisan on 2006-12-22
I used this how to to get Java 1.6 
I would like to say that I am new to all this and I found it easy.
If that's any help...
[http://www.ubuntuforums.org/showthread.php?t=262603&highlight=java+1.6](http://www.ubuntuforums.org/showthread.php?t=262603&highlight=java+1.6)
Forgot the link

---

### Post by dannyboy79 on 2006-12-22
this is what it looks like. really annoyinh! i did check out windows live mail beta though and that works fine? so I guyess I'll just swtich to that but it still makes me wonder why firefox can't display hotmail website? there are just no images. when I click on one of these "not images" the xml code states:<img src="http://gfx2.hotmail.com/tab.separator.on.r.gif"> . does this mean that my computer can't reach this location of the images?? is maybe noscript blockinfg this somehow despite me allowing noscript to allow all scripts for this site? anynire help would be appreciated.

---

### Post by fragos on 2006-12-22
Are you running the adblock extension?  Some sites are now using icons and gifs stored in places like doubleclick which adblock blocks when you use the automated add site list.  I believe this is being done to get people to turn off add blocking from these obnoxious sites.  If you're running adblock you can examine the image sources and will see those blocked are displayed in red.  It could even be Microsoft making sure open source doesn't work right.  I suggest the real solution is a gmail web account which is designed for standards based access.

---

### Post by PurplePenguin on 2006-12-22
I have a feeling that your adblock/script-blocking filter might be catching this as well.  It is strange that something so simple wouldn't be displayed in Firefox... the fact that you've got this kind of filtering software seems to make it the most obvious potential source of the problem.  If there's a way for you to completely disable the plugin and try again, you might tell for sure.

Fragos mentioned getting a Gmail account.  I do agree, although with a twist... Gmail is very easy to get working with email clients (outlook on windows, thunderbird, kmail, evolution, etc).  They make no secret of the fact that it can be used with these programs, and they even have instructions on their site for how to use them.  They even let you use their smtp to send email as well as receive.  So in other words, they're letting you use their service, and you don't even have to go to their website and see their ads. :)

---

### Post by fragos on 2006-12-23
Gmail has great spam filtering.  Spam when identified is saved in a gmail folder.  You can review it on the web if you wish.  It isn't transfered with POP access which I think is just great.

---

