---
title: "New system question..."
date: 2007-12-12
forum: General Help
---

### Post by robhix on 2007-12-12
Hey all,

I am about to build my parents a new PC.  They are probably going to switch over to a broadband internet connection, and they want something simple.  They want something they will not have to fool with too much.  I have been playing around with Ubuntu and I think it would be the perfect solution. However, I am not sure how to set things up.

At first I thought run with a LiveCD and then problems could be fixed simply by rebooting the computer.  I could create a persistent partition on the internal hard drive for data.  Once I got persistence to working on a test system I realized I could not add users and the added user persist.  This would not work for them as I want to set up separate accounts so they cannot mess up the computer.

Not I am on to a hard drive installation.  This of course make recovering from something catestrophic a little more complicated.  Is there a way that I can automatically backup and restore (if needed).

My parents are not computer people.  In fact I am the only one in the family that is relatively savvy when it comes to computers.  I live in Virginia and they are in Tennessee, so I need something dirt simple so when something goes wrong with their system, they can easily restore things (I could be on the phone if needed).

Please share some ideas with me.  I need to know how to proceed.

Thanks in advance, 
Rob Hix

---

### Post by Talon2 on 2007-12-12
This system runs a modified version of Ubuntu called gOS.

[http://www.walmart.com/catalog/product.do?product_id=7754614](http://www.walmart.com/catalog/product.do?product_id=7754614)

I downloaded and tested gOS.  It is about as simple to operate as it gets.

---

### Post by p_quarles on 2007-12-12
A hard drive installation is the only way to go. Running the OS off the live CD full time is a complete waste of system resources (and a minor waste of electricity).

It's easy, though, to prevent them from tampering with anything but their own /home partition: just make non-administrative accounts for them. They won't be able to accidentally do anything that will compromise the integrity of the system itself. Sure, they'll be able to accidentally delete files, but they won't be able to alter xorg.conf, install unknown software, etc.

This does leave the problem of routine administration, though. I see a couple solutions to this, all of which will work.
1) Give your parents an administrative account and password, along with a list of "safe" operations to perform while using this account (e.g., using Add/Remove Programs, updating the system). Instruct them to contact you if they want to do anything that's not on that list.

2) Establish a remote connection so that you can maintain their computer for them. If you go this route, make sure to research the security implications. A sloppy remote access setup can be compromised, but if it's set up correctly, it's safe. 

There are other approaches as well, but these strike me as the easiest for both you as well as your parents, with the least hassle.

---

### Post by linuxlizard on 2007-12-13
Hey, I did something similar with my own folks who also are not computer people and are in their 70s. 

My solution was this- I installed ubuntu, the video drivers, codecs, java, printer and whatnot so they could get video when they wanted it or if someone sent them a link to a greeting card or whatever. 

Next I went into administration and made it so it autologged into my mom's user desktop on bootup so she didn't have to hassle with her user name and password- it auto-logins when she turns the computer on and goes from boot straight to the desktop.

Then I removed the update notification from the panel so when new updates come out my folks are never bothered with the notification bubble or icon to click. Things work fine without updating, and I just update for them when I stop by to visit every month or so. 

Next I simplified the the panels- removed the bottom panel and stuck the window list in the top panel, reduced the number of desktops to 1 so things wouldn't magically disappear on my mom if she accidentally switched desktops and removed the desktop switcher from the panel, and then I made the panel a bit larger and stuck big icons in there- only 3. 1 was for firefox which my parents understand is how they go onto the internet and get their e-mail off the web, etc. 1 was for Abiword which is closer to microsoft word in menu layout than open office is, so is less confusing for my mom and opens much faster than open office writer. and 1 is for shutting the computer off.

That's pretty much all my mom uses the computer for on a daily basis.

Next I stuck two big folder icons on the desktop- 1 for pictures and one for documents. Then I went into the camera app for their digital camera and set it so it downloads the pictures off the camera and into the pictures folder. I also set firefox to download into the pictures folder- that's about all my mom downloads from the internet- pictures of grandkids and the like. Then I set abiword to save to the documents folder.

Put a nice background picture on the desktop and a nice theme.

That's it- worry free, trouble free, no need for admin passwords and logins and the like.

My folks have been using ubuntu for over 2 years now and it's been smooth sailing. Windows- now that was a headache with constant warnings and updates popping up scaring them so they would call me all the time with vague descriptions wanting to know what to do so they wouldn't hurt their computer. But ubuntu- no worries.

PS- I've got gOS running in virtualbox. It's kind of cool looking, but I think it would be confusing and "busy" to my folks. I simplified ubuntu very much- only leaving icons for what they use.

---

### Post by Warren Watts on 2007-12-13
> **linuxlizard said:**
> ....I removed the update notification from the panel.... simplified the the panels....reduced the number of desktops to 1 ....made the panel a bit larger and stuck big icons in there- only 3....stuck two big folder icons on the desktop..
I set something very similar up for the small children that live with me.  I just created an account just for them, with "kids" as the username and an easy to remember password, then simplified the desktop and trimmed the menus down, eliminated all the administration related menu options, and created a few huge icons for ZSNES, TuxPaint, Firefox, etc.., and set them loose. 

I also installed a Firefox addon that blocks adult sites, just to keep the kiddies from inadvertently linking to porn...

Don't get me wrong, I'm not trying to compare your parents to small children... I just tried to eliminate any tempting things for the kids to click on that weren't related to their basic needs.

I attached a screenshot... (My 12 year old daughter provided the wallpaper..LOL)

---

### Post by linuxlizard on 2007-12-13
> Don't get me wrong, I'm not trying to compare your parents to small children

Yeah, well- kids learn this stuff faster than old folks, and the needs are similar. My own kids have been using the computer since they were about 3.

I forgot to add, I installed adblock plus in firefox as well. Gets rid of those ads that look like warnings click to protect your computer or whatever.

---

