---
title: "[SOLVED] Greeter Application crash"
date: 2006-11-03
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-11-03
On My other machine that I run Ubuntu Edgy. It has worked great. Last week I was playing around with wallpapers and I also added Xubuntu-Desktop and then I removed Xubuntu Desk-top. Now when I turn on machine and right before it gets to login screen a message box appears:** " The greeter application appears to be crashing. Attemting to use a different one "**  Can some one help me understand what is happening and a solution please? Thanks

---

### Post by IusedTObeSOMEONEelse on 2006-11-03
**ooPs!** yes I did **BUMP**

---

### Post by IusedTObeSOMEONEelse on 2006-11-03
Bump-Bump

---

### Post by IusedTObeSOMEONEelse on 2006-11-03
Hello!!! Am in the right Forum (Ubuntu) or is this posted on Mars?  haha :-k

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
This is sad that I can not even get a response such as  "Sorry I can not help but..." Oh well, I might as well move on as the problem isn't keeping me from using machine. It's just annoying. Oh my F*%#@*G  hell, is there not one person who will attempt an answer for me? Unbelievable!!

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
Bumpity Bump!

---

### Post by podunk on 2006-11-04
Hey MustangSal! <waves!>

I'm lazy and not very smart, so i would likely put the Xbuntu desktop back. It doesn't take up much room and you don't have to use it.

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
Sound good to me. Thanks, Sally

---

### Post by andy gee on 2006-12-13
Hey Sally,

Hope you haven't done anything too drastic yet! I had this exact problem yesterday. I had been fiddling with the "Log-in preferences" gui and as well as changing to a new log-in screen I changed a few other options as well (sound familiar so far?). 

I eventually figured out which option caused the problem: on the 3rd tab of the gui (labelled "Accessibility"), the first option is "Enable accessible login". I had changed this from unchecked to checked. As soon as I got rid of that tick, I could use whichever login screen I wanted.

Yay! jus' *loooove* having the answer!

---

### Post by Bright Hammer on 2006-12-26
Thanks for the answer it was driving me ](*,) crazy.

---

### Post by andy gee on 2007-01-19
I just received a message which alerted me to the fact that my post is missing some information, so here goes a step-by-step guide:

In steps following, I'm assuming you're using ubuntu gnome with no menu modifications.

1. Click on the 'System' menu (next to 'Applications' and 'Places') and select 'Administration'. Find the 'Login Window' option and click on it.

2. A GUI will start titled "Login Window Preferences". Select the third tab, 'Accessibility'.

3. The very first option is "Enable accessible login". If you have a greeter crash error and this box is checked, unchecking it worked for me. Hope it works for you!

---

### Post by xhabitat4humanityx on 2007-02-13
:KS  Same problem...This worked for me as well. THANKS!

---

### Post by Milner_07 on 2007-03-10
I had the same problem and it worked for me to. Thanks so much!

TM

---

### Post by phefferan on 2007-03-16
This worked for me also. Thanks.

---

### Post by ubromtoo on 2007-03-25
Andy Gee :

    thank you so much, gone is the slooow boot-up, and my chosen greeter

application works just fine!  a gold star :KS  for you :)

---

### Post by Mr. Nefarius on 2007-03-29
:KS :KS :KS  Right On!  Thanks :-P

---

### Post by User101 on 2007-04-07
> **andy gee said:**
> I just received a message which alerted me to the fact that my post is missing some information, so here goes a step-by-step guide:

In steps following, I'm assuming you're using ubuntu gnome with no menu modifications.

1. Click on the 'System' menu (next to 'Applications' and 'Places') and select 'Administration'. Find the 'Login Window' option and click on it.

2. A GUI will start titled "Login Window Preferences". Select the third tab, 'Accessibility'.

3. The very first option is "Enable accessible login". If you have a greeter crash error and this box is checked, unchecking it worked for me. Hope it works for you!

Thank you very much for posting the solution. A positive side-effect that I noticed is the ability to Switch Users once again (it had stopped working at the same time as the Greeter error message appeared). 

Having said this, it seems to me that it would be good to enable Accessible Login without the Greeter errors and User Switching problems. I think that it is important  to make computers accessible for people with disabilities -- and keep them  accessible. Inability to Login at all due to a disability would be worse than the occasional application not working correctly if you turn accessibility features on after Login. Just my 2-cents.

Has this been documented as a bug, and if so, how does one find out? If not, how does one submit a bug about this issue?

---

### Post by andy gee on 2007-04-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/55566](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/55566) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi User101, and thanks for your interest!

I agree that my guide is only a work-around and does not fix the bug. It has been reported at [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/55566](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/55566). There is a lot of information there about Ubuntu and accessible log-ins, and if you need an accessible log-in,  you might find a proper fix there (i.e. a way of not crashing the greeter application while keeping accessible log-in).

In general, if you have a bug that your Ubuntu based OS does not automatically offer to report  for you (like this the bug we are discussing here) you can go to [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu). 
1. Click on the tab labeled 'Bugs'. 
2. Click on "Report a bug" (top left).
3. Enter a short description about bug - as an example, try "Greeter application crash".
4. Have a look at a few of the summaries. Currently, the third one down, number 55566, titled "The greeter application appears to be crashing with 'Enable accessible login'" is the one most similar to the bug we would be reporting, so click on that.
6. Scroll down the comments. You'll see that this indeed is the problem we are seeing, and some of the replies give the authors thoughts about what might be causing the problem and how to try to fix it.
7. If the bug is not similar to any of the ones listed, continue below on the original page and give more details on the bug.

It's actually a lot simpler than it might seem from what I've described here, and it's a simple way of reporting bugs. Try to make sure you give all the information you can, and if someone asks for more information, please help by doing so - it'll help Ubuntu, and you'll learn quite a bit in the process! For more information on Bug posting, go to: [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

Since I am a bit of a n00b myself, if I have made any mistakes in the above info please correct me.

andy gee

PS: Thanks everyone for your positive comments - it makes posting these little help notices so much more rewarding to know that people are actually getting help from them! 

):P

---

### Post by User101 on 2007-04-08
Thank you very much for your prompt, constructive and detailed reply. Here's another star to add to your collection: :KS

If I may add one small point, Ubuntu Launchpad seems to require a separate login from Ubuntu Forums. You need to go through (yet) another registration process before you can post a bug or discuss one. Oh, well, you can't have perfection! ;-)

In general, it's a real pleasure -- and a refreshing change -- to find a technology-oriented community that is so welcoming, helpful and constructive! :grin:

---

### Post by andy gee on 2007-04-11
--OFF TOPIC--

Yeah, the constant requests for registration do get annoying. However, if site-owners don't do this, they would soon get spammed beyond hope of repair so I don't mind it mostly. As to why you need a separate registration for Launchpad and Ubuntu, I think Launchpad bug-tracks for other software apart from Ubuntu, so they can't simply import all the Ubuntu registrations. I guess you could just use the same username and password as for your Ubuntu account. when you register.

As a side note, if your registration is just for midnight porn browsing and you're using Firefox rather than epiphany, get the Trashmail extension. Once you've installed it into Firefox, it adds an option onto your context-sensitive (right mouse click) menu which allows you to use a throw-away webmail address.

This account lasts for about a week or so - just long enough to get a look at whatever you want, without having your own email address spammed.

I've found it great so far - see what you think.

---

### Post by Killane on 2007-09-13
Is there a way to reset my login system to it's default settings via recovery mode?
I managed to activate a theme that for some reason makes my Feisty laptop hang while trying to load the login screen and if I can just reset it back to the default settings I promise I won't touch it again until I know what I'm doing quite a bit better.

---

### Post by cipher27 on 2007-09-28
If the GUI fails to load and you are unable to access the system menu then  you should try the instructions below.

1. first reboot your computer into maintenance mode/recovery mode.

2. open /etc/gdm/gdm.conf-custom by entering the following command

sudo vim /etc/gdm/gdm.conf-custom

3. press i to enter into insert mode. Locate the following line and comment it by inserting a # in front of the line.

[COLOR=black]GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener[/COLOR]

4. press the Esc key and then type in :wq to save and quit the editor.

5. type sudo init 6 to reboot

hope this helps

cipher27
________________________________________________________

[Http://liltux.wordpress.com](Http://liltux.wordpress.com)

---

### Post by askarir on 2007-10-10
Hi

 I can't log into the gui at all, after putting the username and password it tries to start up. It appears the monitor is resizing and then goes back to the login prompt.

I have received the "Greeter Application crash" message once when logging in.

I've checked /etc/gdm/gdm.conf-custom but all i have is the # comments at the top followed by section headings.

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]



I need help. Not sure what info would be useful as I very new.

TIA

Arms

2.6.15-29-server

----

update: i changed the greeter to gdmlogin same problem ... is there logs anywhere that would help track this down .... should i start a new thread?

---

### Post by Budward on 2007-10-31
I have exactly the same problem as asakir. I'm very confused by the whole thing. Any help would be very much appreciated.

---

### Post by askarir on 2007-10-31
i haven't managed to fix it yet, as i'm using my machine to run vmware i don't really need the desktop  but its annoying that it isn't working.

if i manage to fix it i will update you this thread.

---

### Post by mnarinsky on 2007-11-26
Check how much free space do you have left on your hard drive ("df" command could be helpful).

I had 100% used and I had this message.
Cleaning up the hard drive solved the problem..

---

### Post by askarir on 2007-11-28
Thank you very much mnarinsky, a lack of free space was causing the problem on one of my partitions. 

I had no reason to check because everything else was actually working without issue, I was using SSH for when I needed to do anyting to the box.

But its fixed now, and again thank you :)

---

### Post by shafi on 2008-02-04
to solve the problem of Greeter application appears to be crashing follow the link To Enable Accessible Login:

[http://www.gnome.org/learn/access-guide/2.10/apa.html](http://www.gnome.org/learn/access-guide/2.10/apa.html)
[http://www.gnome.org/learn/access-guide/latest/sysadmin-27.html](http://www.gnome.org/learn/access-guide/latest/sysadmin-27.html)

---

### Post by Vishawjeet on 2008-02-05
How to solve this problem in ubuntu.

---

