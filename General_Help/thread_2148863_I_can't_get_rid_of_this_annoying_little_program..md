---
title: "I can't get rid of this annoying little program."
date: 2013-05-26
forum: General Help
---

### Post by Moose on 2013-05-26
I installed Conky the other day, and I want to get rid of it. But no matter what I do, it just won't go. I removed it using synaptics, I tried using <sudo apt-get remove conky> and <sudo apt-get autoremove conky< and it still runs at startup. It is really irritating because thanks to this program, my wallpaper won't show and all I get is a really ugly grey background. pls halp? DDDD:

Thanks. c:

---

### Post by HermanAB on 2013-05-27
$ sudo find / -name conk*

and go from there

---

### Post by HiImTye on 2013-05-27
```
sudo apt-get remove conky*
```
conky is only a metapackage that references another package

---

### Post by Moose on 2013-05-27
I tried both of those commands, but this stupid program is still on my computer. It's annoying the heck out of me because it's stupid grey background is there and it is just bugging me.

---

### Post by vasa1 on 2013-05-27
It's possible that you have some other problem. Put up a screenshot of what annoys you.

---

### Post by Moose on 2013-05-27
[IMG]https://imageshack.us/scaled/large/825/screenshotfrom201305271.png[/IMG]

---

### Post by Moose on 2013-05-27
It's just that damn background. My actual wallpaper won't show.

---

### Post by ppv on 2013-05-27
Maybe you should turn off those privacy settings that you have used for your screenshot upload... can't view your screenshot.

And what happens when you try to manually set the wallpaper, does it change or still remains they gray you say.

---

### Post by Moose on 2013-05-27
I have no privacy settings on it?
Anyway, what happens is, when I click on "Activities" in the Gnome Panel, I can see my wallpaper in the background, but when I go to the actual desktop itself, it goes grey. 
And when i change the wallpaper it makes no difference.

---

### Post by ppv on 2013-05-27
Hmm...this is what I get when I click on your attachment.



[h=2]vBulletin Message[/h][COLOR=#000000]Sorry, this user has chosen a privacy option that prevents you from viewing this information.
[/COLOR]
[COLOR=#000000]Ubuntu Forums





Also, do you see some conky in the process list. Try the below from a terminal and if you see something conky in it, kill the process.

ps -eaf | grep -i conky

pkill <the_name_of_process_you_see_from_above_output>[/COLOR]

---

### Post by Moose on 2013-05-27
Still didn't fix it. :c

---

### Post by ppv on 2013-05-27
> **Moose said:**
> Still didn't fix it. :c
the attachment or the process kill?


If it's about the process kill, did you see anything conky related in the output. It seems something trivial is missing/altered in your case but can only help so much based on the limited information.

---

### Post by Moose on 2013-05-27
When I input your command, I got this:
<anthony  14310 13987  0 19:04 pts/1    00:00:00 grep --color=auto -i conky>

I typed the other command to kill it, and the white background still didn't disappear.

---

### Post by whatthefunk on 2013-05-27
First, try to purge conky:

sudo apt-get purge conky

If that doesnt work, remove it from your startup program list and delete all your conky files.

---

### Post by Moose on 2013-05-27
I purged it, and it did something. And how do I remove it from start up?
And would I have to go searching for EVERY file? :c

Sorry, I'm not good at this stuff.

---

### Post by groggin on 2013-05-27
> **Moose said:**
> I purged it, and it did something. And how do I remove it from start up?
And would I have to go searching for EVERY file? :c

Sorry, I'm not good at this stuff.

   system>preferences>startup applications :-)
      - and no!

---

### Post by whatthefunk on 2013-05-27
I dont use Ubuntu, so I really have no idea how to remove things from startup.  Maybe type "startup" in the dash to see if anything comes up?  If not, see if you have a .config/autostart directory in your home folder and delete the conkey entry.  If you delete the autostart file, you shouldnt have to delte everything else....your main problem seems to be that it starts up when you dont want it to.
Hopefully somebody who uses Unity can come on and give you clearer instructions.

---

### Post by Moose on 2013-05-27
I searched "startup" and an application was shown, I opened it and conky wasn't there. So I'll just try editing the file manually when I get home.

---

### Post by HiImTye on 2013-05-27
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
if this returns nothing then you don't have conky installed
```
apt-cache policy conky* | grep \*
```

---

### Post by Moose on 2013-05-28
And what if I don't have Conky installed but my wallpaper is still this ugly grey background? What then?

---

### Post by whatthefunk on 2013-05-28
You have of course tried to change the wallpaper?

---

### Post by BlinkinCat on 2013-05-28
> **Moose said:**
> And what if I don't have Conky installed but my wallpaper is still this ugly grey background? What then?


It would be really annoying but maybe a fresh install?

---

### Post by Moose on 2013-05-28
> **whatthefunk said:**
> You have of course tried to change the wallpaper?

Dude, that was the first thing I did. -.-

---

### Post by mcduck on 2013-05-28
> **Moose said:**
> And what if I don't have Conky installed but my wallpaper is still this ugly grey background? What then?

Then make sure whatever program is supposed to draw the desktop for you is still running and configured correctly.

For Gnome (& Unity), the program in question would be Nautilus. Check that the desktop/background/draw-background is enabled in dconf.

(If you don't have dconf-editor enabled then you can running "gsettings set org.gnome.desktop.background draw-background true" in a terminal should do the job)

---

### Post by whatthefunk on 2013-05-28
You could also start a new user account and see if the problem persists there.  this would tell you if the problem was local or system wide.  My feeling is that its local so deleting the correct system file could reset the wallpaper and fix the problem.

---

### Post by Moose on 2013-05-28
I didn't make a new user account, but I logged in using the guest account and I had the same issue.

---

### Post by BlinkinCat on 2013-05-28
> **Moose said:**
> I didn't make a new user account, but I logged in using the guest account and I had the same issue.


If I was you I would try a new user account - it may show up something.

You can always delete it later as far as I know.

---

### Post by groggin on 2013-05-28
[Quote=Moose] I purged it, and it did something. And how do I remove it from start up?
And would I have to go searching for EVERY file? :c

Sorry, I'm not good at this stuff[/quote]

.
system>preferences>startup applications
- and no! 

[Quote=Moose]I searched "startup" and an application was shown, I opened it and conky wasn't there. So I'll just try editing the file manually when I get home.[/quote]


   i'm sorry, i should have said go to the menu button, then system>preferences and you'll come to startup applications, clicking that should bring up a dialog with most of the apps you have installed. if conky isn't there, clic [add] navigate to /usr/bin and perhaps you'll see it there.
g'luck mate ;-)

---

### Post by Moose on 2013-05-28
Okay, so I've re-installed it and uninstalled it more than once, and I still have this issue. I am 100% sure that Conky isn't on my computer anymore. I'll explain in further detail what happens:

1. I log in.
2. Everything loads
3. My wallpaper loads
4. 3 seconds later, my wallpaper disappears and is replaced by a white/grey background
(5. (I am using Gnome) when I open the activities menu, my wallpaper is visible in the background.
6. When I return to the desktop, no wallpaper.)

---

### Post by dodo3773 on 2013-05-29
> **Moose said:**
> When I input your command, I got this:
<anthony  14310 13987  0 19:04 pts/1    00:00:00 grep --color=auto -i conky>

I typed the other command to kill it, and the white background still didn't disappear.

The output here says that conky is not running. It only shows conky as it related to you grepping it with ps. That is why you were not able to kill it. Your issue is coming from somewhere else. Did you do anything different to your system recently? Like update something or disable / enable anything else? Nautilus used to set the background in gnome I am unsure if this is still the case. You may also want to look into metacity settings or gtk3 theme settings if you haven't updated your system recently. But either way it doesn't look like it's conky unless conky is running under some different process name (highly doubt that).

---

### Post by dodo3773 on 2013-05-29
Does this look familiar? Like it may be your issue:

 [https://www.youtube.com/watch?v=NJOoQPHSgxo](https://www.youtube.com/watch?v=NJOoQPHSgxo)

---

### Post by Moose on 2013-05-29
> **dodo3773 said:**
> does this look familiar? Like it may be your issue:

 [https://www.youtube.com/watch?v=njooqphsgxo](https://www.youtube.com/watch?v=njooqphsgxo)

i love you! Thank you so much that solved it!

---

### Post by dodo3773 on 2013-05-29
You're welcome. Happy to help. Glad you sorted it out.

---

### Post by Moose on 2013-05-29
n.n

---

### Post by gleedadswell on 2013-05-29
I agree with ppv that first you should use ps (or top) to verify that conky is actually running.

If you do find that it's running then a simple thing to look into is whether it is in the list of applications that run on startup.  You may be able to solve your problem just by removing it from there.

---

### Post by Moose on 2013-05-30
Dude, my problem is fixed now ahaha. It appears that maybe Conky adjusted a setting when I installed it. Dodo3773 helped me out.

---

