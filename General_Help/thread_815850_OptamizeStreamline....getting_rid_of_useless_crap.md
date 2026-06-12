---
title: "Optamize/Streamline....getting rid of useless crap"
date: 2008-06-02
forum: General Help
---

### Post by darussian12 on 2008-06-02
coming from an XP world and playing with the ubuntu version 2 versions ago before giving up and coming back...im used to having to do extra stuff to make my bloated MS OS run better....searching for keywords i though were relevant in my case i couldnt find anything so my issue is...

1) im used to having to disable useless tasks in the background like print spooler and all the other services i never need, google found me a link to disable the services through system-->admin-->services...the only thing is there are a total of 17 there now and i have all the ones i can have disabled...are those really the only things i have running in the background that i can turn off if i dont use?

2)disk clean up/defrag....i never used the built in windows utility but had 3rd party apps that did way better..but is ubuntu so "great" i never have to worry about defrag/clean up of junk files or how would i do it periodically...

3)registry edits/cleanup....again i always used 3rd party utilities in XP to get rid of random obsolete registry points...in ubuntu  when i use synaptic to remove a program i always use the option to "mark for complete removal"...does that do what i need and leave no random crap for that app on my system or who do i go about doing routine main to get rid of random leftovers from obsolete programs over time if thats even needed in linux?

4)HOW THE HECK DO I DISABLE GETTING PROMPTED TO ENTER MY PW TO INSTALL/REMOVE ANYTHING....this brings back nightmares of VISTA getting harassed to do the simplest things to enter my PW...is there a way to disable ever having to enter my PW, whether being logged into sudo from the start or whatever...im the only one that uses my laptop and have no desire to keep entering a PW to install an app from terminal or doing synaptic or altering some other system setting. i want to be able to have system wide admin privileges from the moment i login w/o ever having to enter my pw at all to do anything to my pc after I am logged in.

5)how the heck do i change desktop settings...the default ubuntu icon sizes seem like they are for blind people...how do i go about changeing icon/text size...searching "desktop" or "desktop icons" brought up way too many results for me to sift through

6)along the lines of my 1st question...how can i disable startup crap or is that the exact same thing as services...or even how do i find out what starts up on bootup...like say i have the network manager applet starting...how would i go about disabling that thing from starting and appearing...i know how to remove it from the task bar but how would i stop some useless app/service from loading up on bootup...im sure 1 and 6 are related but in MS world startup apps were accessed differently from background services so just covering my bases :-)

thanks all...some questions might be irrelevant for linux use but i wanted to know and some might have a different term but let i appreciate you all that help me with any of the ?'s

---

### Post by sdennie on 2008-06-02
1) I wouldn't worry about it.

2) I wouldn't worry about it.

3) Using purge will erase all system level config files.  It will not remove stuff in your home directory but, in the vast majority of cases, the only thing it will leave around is a text file that is like 10k.

4) Hopefully, you can't.  There is a very good reason why Ubuntu prompts you for passwords: It makes the system more secure.

5) If you are talking about nautilus, you can probably change things with Edit->Preferences.  If not, you can go hardcore and hit Alt-F2 and type, "gconf-editor".  Navigate to /apps/nautilus and see what you can find.

6) Have a look at System->Preferences->Sessions.  If that doesn't do it for you and you really know what you are doing, you can remove symlinks from /etc/rc5.d to prevent things from starting.  You almost certainly won't need to do that though.

Edit:
My humble advice to you would be this: Ubuntu is not Windows.  Don't try to fix something unless you are sure it's broken.

---

### Post by darussian12 on 2008-06-02
1 & 2) prob right and thats what i wanted to double check on. i use my pc for video converting and working with over 4gig size files converting to a DVD image non stop didnt know if linux works that much better with hd usage to not worry about it. and i try random apps and install/remove pretty much daily stuff i try and dont like so didnt know if i needed to do anything other then select the "remove completly" option in synaptic

3)you're over my head on that cause i know how to do basic stuff with ubuntu..but i assume "purge" is something extra i type in terminal when i do a command?

4)i never understand this from people when they say it...i dont care about making my system secure...i want it convenient to use...if i decide to open security holes on it then why not?...i dont store anything imp on my PC...i do a clean install of my OS prob once if not twice a year and back up files i cant lose regularly...if i leave my PC open for you or the guy next door to take over and control it then go for it...i have nothing for you to want...i just want my usage to be as hassle free as possible.

5)this changes the FOLDER view...im looking to alter the desktop view where i see my wall paper and related icons..i still havent figured out how to do basic stuff like changing the sizes for desktop icons...how hard can it be...obv i guess hard enough for a linux retard like me not to figure it out

6)pretty much pointed me to what i was looking for in sessions...

and yes i get that ubuntu is not windows...i just know i had a hell of a time getting hardy going anf trying to get my self ready for any unexpected events in the future or keep myself from coming across unexpected problems....so far so good for prob 90% of things i need...still dont have wless or the builtin webcam working but thats for another thread prob. im just trying to keep myself ahead of things that caused me probs in the other OS if they are possible in linux even

---

### Post by sdennie on 2008-06-02
3) Sorry, I was using command line terminology on that.  What you are doing in synaptic is the equivalent of "sudo apt-get purge whatever" and, is a very clean way to uninstall something.

4) I don't mean to sound crass but, I'll not help you to make your system do that.  It's possible but, it's such a horrible idea that hopefully no one will tell you how to do it.  If you research how to do it, you'll eventually find that typing in passwords is not actually that common and, there are many, many reasons why it's a good idea to have Ubuntu setup the way it is.  I'm perfectly happy to give insane advice to people but, this is one area where I won't bend.

5) It sounds like you are fairly proficient with Windows.  By default, gnome purposely provides a limited number of configuration options.  If you use the ALT-F2 then gconf-editor option I mentioned, you will probably eventually find what you are looking for.  In fact, for someone who really enjoys tweaking their system, gconf-editor is a really fun way to tweak things.  It's more fun in that it's just a specialized XML editor (unlike regedit) and in the unlikely event that you absolutely break something, removing the offending file in ~/.gconf will just restore it to its default.

Welcome to Ubuntu.  ;)

---

### Post by darussian12 on 2008-06-02
sweet...you got #3 down....4 i guess ill find else where or another poster will let me know...

5)kinda there...im looking for a way to just change desktop settings..whether size of icons or the icon text or adding app shortcuts...figured out i cant just drag from the "start" menu the apps i want to the desktop cause the ones i drag i can open but it displays info from last time i had opened...ie i dragged the axurues app from the internet menu to the desktop and clicking the azurues icon on the desktop i just crated it opens azurus but the app shows the exact same D/L rate i was before i closed it and it doesnt change and progress stays the same...but i figure i can do the "create shortcut" command...im to the point now im nit picking about unessential stuff, but just stuff i want to know and would like to use...since the nautulus settings you gave me ive been able to change the font to be as tiny as i want but the icons i cant make any smaller even when i change the "icon size" in the command you gave me even after a reboot in case i had to log out of the window system for it to take effect...is there any sort of unified "system manager" of sorts for ubuntu where i can change setting for anything?...i have "ubuntu tweak" installed now but that gets me access to some of the things i want w/o having to do command promt stuff...


thnx for all you other help for far VOR

---

### Post by sdennie on 2008-06-02
Unfortunately, I don't think I can help any more.  I'm mostly a command line guy.  I looked briefly at Gnome Tweak and it looks like it's a cool frontend to configure common gconf stuff.  It's possible to change/remove/break essentially anything with Ubuntu.  Using gconf-editor is a good start for real customization but, there are so many things you can do to your system that I think only google can answer your questions.

---

### Post by cariboo on 2008-06-02
It is fairly easy to run as root. You'll have to figure that out yourself. The reason nobody but a newbie runs things as root is that you can damage your system especially if you don't know what you are doing. Anyway what's so hard about entering a password once in a while, it becomes habit after you've been doing for a while.

From the what you typed in this thread you seem to be fairly competent at running windows, but Linux isn't windows and virtually nothing you know is transferable.Check this link out if you really want to learn the hows and whys of Linux:

[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

---

### Post by kaboodle_fish on 2008-06-02
> **darussian12 said:**
> 5)kinda there...im looking for a way to just change desktop settings..whether size of icons or the icon text **or adding app shortcuts**

Just right click on the menu entry you want to add to the desktop and you will have the option to add it to either the panel or the desktop

---

### Post by HunterThomson on 2008-06-02
About #4..............

It that it would open a security hole...... It is that you will have no security at all......

This is not like window$ where you are screwed anyway so that password is just a wast of time. That password is the whole game on an Ubuntu sys. Not only should you not change it but your password should be like 18+ carictors long and use leters # and %$#@.... like 

Hi$Ilike123%you)bob3

if your password is bob123.... Anyone can crack it in less then a sec.

As for not having anything on your computer that is worth anything, you never buy anything online? Well even so, your computer is something... 

You should learn some more about what crackers can do....

---

### Post by tropdoug on 2008-06-02
Not sure if this helps with you dektop icons size issue, but I found right click on the icon, brings up a menu, about half way down is "stretch icon" click and enlarge or reduce your icon size by dragging with the mouse. Add whatever text you want into the name box after clicking on "properties" in the original drop down menu. 

as a fellow convert, my suggestion re your Pwd issue, don't try to break a great system. it really is not windows and that is both its good point and its bad. You can configure or break ANYTHING in this OS and that is what makes it so powerful Be a Man learn a new way lol

---

