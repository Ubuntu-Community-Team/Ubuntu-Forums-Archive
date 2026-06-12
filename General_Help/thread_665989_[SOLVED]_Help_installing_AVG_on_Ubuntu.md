---
title: "[SOLVED] Help installing AVG on Ubuntu"
date: 2008-01-12
forum: General Help
---

### Post by Sabar on 2008-01-12
Hello every one I am trying to load AVG anti-virus to my Ubuntu 7.10.

I have gone to the AVG site and just clicked where I thought it would automatically download and all I got was a page that took forever to load with a bunch of funny looking symbles on it. [AVG download page]("http://free.grisoft.com/doc/5390/us/frt/0?prd=afl") 

So then I started searching for directions. You know, when all else fails, read the directions. so I went to the AVG help site. and found this page [AVG Help]("http://free.grisoft.com/doc/5/us/frt/0/num/652#faq_652")

Well I dont understand exactly what it is I am trying to do. but I got no were there either. So now I I start searching on these forums. and I found anouther great artical that I think for sure will help me [Forums page for loading AVG]("http://ubuntuforums.org/showthread.php?t=136064")

Guys I am still lost. on the forums page it has this. 

> Before Installation

Make sure that your sourcelist is set up correctly. If you are in doubt make a search on the forum.


I did a search and came up empty could some one explain this to me? whats a sourcelist?

Next when I clip and past any of this into the terminal

> $ su
# dpkg -i avg75fld-r{version}-a{version_of_avi}.i386.deb
# /opt/grisoft/avggui/bin/avggui_update_licinfo.sh
# exit
$ avggui &



I get nothing!

 > alien@alien:~$ $ su 
bash: $: command not found


> alien@alien:~$ # dpkg -i avg75fld-r{version}-a{version_of_avi}.i386.deb

Nothing happened here.

I just tried this also > alien@alien:~$ sudo apt get avg75fld-r50-a1236.i386.deb
[sudo] password for alien:
sudo: apt: command not found

Guys I am missing something really easy I just know I am any help would be appreciated.

Thank you every one
Sabar

P.S. Why are my links not showing up blue and underlined?

---

### Post by GavinZac on 2008-01-12
> **Sabar said:**
> Hello every one I am trying to load AVG anti-virus to my Ubuntu 7.10.May I ask why? It seems rather excessive, given that the majority of viruses AVG will target cant actually run on your machine.
> I did a search and came up empty could some one explain this to me? whats a sourcelist?You need to add it to the list of sources Synaptic can download from. Do this in the Synaptic applcation, in the menu

> Next when I clip and past any of this into the terminal
I get nothing!
Nothing happened here.

I just tried this also 

Guys I am missing something really easy I just know I am any help would be appreciated.

Thank you every one
Sabar

P.S. Why are my links not showing up blue and underlined?
the problem is, that you're pasting everything! you should just be pasting everything AFTER the $dollar sign. People do this to indicate that you are running these commands in user mode rather than root mdoe (#). The error you are getting is telling you it doesnt know what to do with the $dollar.

---

### Post by ramjet_1953 on 2008-01-12
Of course, it is your decision to install an anti-virus program on Linux, but I agree with GavinZac.

Why do you need it?

Unless you are forwarding-on emails that have Windows executables attached, you are wasting HDD space and processor time.

Even if you are forwarding emails to Windows users, most email providers have built-in virus scanning anyway.

Let go of your Windows mentality and enjoy the security and stability if 'NIX.

Regards,
Roger :cool:

---

### Post by jrusso2 on 2008-01-12
AVG is easy to install.

Download the .deb file to your home directory,  Open nautilus and browse to the package.

Right click on the package  and choose install with gdebi from the right click menu

It will ask for your password and its done.

---

### Post by oldos2er on 2008-01-12
"su" doesn't work because Ubuntu doesn't create a root account. Use sudo instead.

 The command you need is apt-get, not simply "apt."

 Unless you're going to be exchanging files with Win* users, you really don't need an antivirus program.

---

### Post by lizadove on 2008-01-13
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)  This is the best installation guide I've come across.  It's long, but you'll learn a lot about ubuntu and what your commands mean - if you're new to ubuntu like me. :)

---

### Post by HermanAB on 2008-01-13
Maybe you should also read this:
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

Cheers,

Herman

---

### Post by Nero_Flint on 2008-01-13
Don't worry about AV software. Just use VirusTotal if you're worried about sending virii to your Windoze friends.

It's a waste of your PC's processing time to run an AV security blanket if it isn't needed. 

It's like sucking your thumb as a 35 year old just because it makes you feel better about your situation. Don't bother.

---

### Post by Sabar on 2008-01-13
Well I guess the best reason I have for wanting to install A-V Protection is becouse Maximum PC told me to. Ok Yea even I think that is weak. actually I am duel booting with XP and I dont want to put things on the computer that I thin open with XP and screw things up. 

On top of that I just am not the most trusting person in the world.  Especially As Linux gets more and more popular. unfortunately I am sure not only the good Windows people will migrate this way but also the losers. Who make the viruses in the first place.

Thanks for so many responses guys I have allot of reading to do and I have to figure out this
> 
You need to add it to the list of sources Synaptic can download from. Do this in the Synaptic applcation, in the menu

Thanks again

---

### Post by Sabar on 2008-01-18
Not exactly sure what I am doing wrong.

Step one.   
           
       I am going to this web page 


Step Two.

       Look under Installation files and click on the blue>  Debian based distributions (Debian, Ubuntu)

ERROR all I get is my computer momentarily freezes then the page comes up with a bunch of odd looking block symbols.  Well this can not be right. Ok time to try the command line.

Step one.

    Open Terminal

Step Two. 

     Read installation notes found on above website under Documentation.( ok really lost after that.)

At this point I blindly try different things in Terminal ( Yea I know this is dumb,) 
> 
alien@alien:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
> 
alien@alien:~$ apt-getavg75fld-r50-a1236.i386.deb
bash: apt-getavg75fld-r50-a1236.i386.deb: command not found
> 

alien@alien:~$ apt-get avg75fld-r50-a1236.i386.deb
E: Invalid operation avg75fld-r50-a1236.i386.deb

Can anybody help me with this? I know the general idea is that there are no Virus's out there that can affect Linux. Well Yea I am a little over cautious I know but part of it is I also duel boot and swap files between the two sometimes. 

Has anybody read the Book Ubuntu 7.10 unleashed?  Is it any good? does it help people who know nothing?

Sabar 
Thanks every one

---

### Post by oldos2er on 2008-01-18
When you're the AVG download page, right-click on the Debian-based distributions, click on 'Save Link As...' Choose to save it to your desktop or wherever. Once it's downloaded, click it to install.

---

### Post by Sabar on 2008-01-18
Oh dear god I really hope it is not that simple..  

Thank you very much

Oh my god its down loading LMAO. OK now I feel like an idiot. thank you so much.

Sabar

---

### Post by oldos2er on 2008-01-18
Glad it's working. If you have any problems installing, please post back.

---

### Post by Casual Fan on 2008-01-19
You realize you've spent more time trying to get AVG to work than you would actually removing a virus?

---

### Post by BuntuFreak on 2008-02-02
First, AVG Free is indeed available for Linux. Yes, they had stopped offering free version for Linux. YES, they have started doing so again. And they have a separate distribution for debian based systems.

I have used AVG Free on my Windows desktops for as long as I can remember. I will not say any more since I'm not a mouthpiece for Grisoft. 

If you are like me and have set up AVG on your Gutsy desktop, I need your help. I cannot get AVG to update through the GUI when I launch it from my desktop or menu shortcut. I can do "sudo avggui" in a Terminal, and sometimes I'm asked for a password and sometimes not (how does sudo decide when it needs a password?). THEN , the update button works in AVG. But if I simply launch from shortcut it fails saying "...you do not have permission to do AVG update..."

So I thought I would outsmart it. I changed the command line for my shortcut to "sudo avggui" since it only said "avggui". Now, it will not even launch through the shortcut. My guess is it is waiting for me to provide password (again, when does sudo want one and when not?). And I have no mechanism to provide one - there being no Terminal window - it simply fails. 

Is this an AVG issue in particular or my lack of understanding of Linux in general and Ubuntu in particular? How do I launch a program using a shortcut that seems to need "administrative" access?

Thanks in advance for any pointers.

---

### Post by Sabar on 2008-02-08
I finally got mine working. I keep forgetting that i am not using windows anymore and things are actually easier in Ubuntu. over thinking things ... go figure. 

I dont know how to get it to work mine has been working fine.

Thanks every one who posted.

---

### Post by dtgolder on 2008-02-20
> **BuntuFreak said:**
> ...I cannot get AVG to update through the GUI when I launch it from my desktop or menu shortcut. I can do "sudo avggui" in a Terminal, and sometimes I'm asked for a password and sometimes not (how does sudo decide when it needs a password?). THEN , the update button works in AVG. But if I simply launch from shortcut it fails saying "...you do not have permission to do AVG update..."....

Had the same issue, and after some research here's what worked:

a) Add yourself to the "avg" group:
System...Administration...Users & Groups
Enter your sudo password
Click on "Manage Groups"
Find the AVG group, click on it and then click on "Properties"
Click on your user name (and any other user that my be running the update) and then click "OK"

b) The tricky part--restart your computer. AVG (apparently) needs a restart to "see" the changes to the user groups.

At that point, you should be set.

Hope this helps (it worked for me)

---

