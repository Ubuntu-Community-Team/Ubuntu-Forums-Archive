---
title: "root autologin possible?"
date: 2007-08-17
forum: General Help
---

### Post by ProN00b on 2007-08-17
ok, first let me explain that i perfectly know of the danger of running as root:
1. possibility of getting whole machine owned by intrusion
2. possibility of ******* stuff up
3. people who think they know whats best for you make their programs not behave/work on root.

well, i seem to be having problem No.3 at the moment, because it doesn't seem to be possible to set autologin to root on gdm... and if i do it over the config (gdm.conf-custom) it just refuses to work.
so my question is how do i get gdm to autologin as root, OR how do i safely migrate my root profile to a normal user without f***ing stuff up. (moving and chowning doesn't seem to work, seems to loose desktop icon placement and user and group admin tool seems to not work anymore (displays no users))

---

### Post by aysiu on 2007-08-17
So let me see if I can get this straight. You've been logging in as root for a while now. You have all your preferences set in the root account (desktop icon arrangement, wallpaper, etc.).

Now you would like to autologin. Either have the account you've been using (root) autologin or have a regular user account autologin... but with root's settings.

---

### Post by ProN00b on 2007-08-17
> **aysiu said:**
> So let me see if I can get this straight. You've been logging in as root for a while now. You have all your preferences set in the root account (desktop icon arrangement, wallpaper, etc.).

Now you would like to autologin. Either have the account you've been using (root) autologin or have a regular user account autologin... but with root's settings.
exactly!

---

### Post by aysiu on 2007-08-17
Moving from /root to /home/*username* and *chown*ing **should** work, but I wouldn't move everything, only the folders that matter.

Since you talk about GDM and haven't mentioned Xubuntu, I'll assume you're using Gnome. If that's the case, log in as root and have two file browser windows open. In the first window, go to /root and press Control-H to see the hidden folders. In the second window, go to /home/*username* and press Control-H.

Before you copy a config folder from /root to /home/*username* (henceforth referred to as ~/), delete the ~/ config folder first. For example, if you're copying /root/.mozilla to ~/.mozilla, delete the existing ~/.mozilla *first*.

I'd say some of the key folders to copy over would be:
/root/.config
/root/.gnome
/root/.gnome2
/root/.gconf
/root/.gconf.d
/root/.metacity
/root/.themes
/root/.icons
/root/.mozilla
/root/.evolution

---

### Post by bodhi.zazen on 2007-08-17
From your previous post, I assume you have enabled root logins already (if not re-post)

To enable auto login : 

Go to System -> Administration -> Login Window

Under the security tab select auto login and user name (root)

You might also want to enable timed login with the same name (otherwise this works only at boot or with restarting gdm)

I use timed login of 10 sec, then you can log in as another user if you want.

---

### Post by ProN00b on 2007-08-17
thats exactly what i been saying if you listen closely, 
"Go to System -> Administration -> Login Window

Under the security tab select auto login and user name (root)"
does not work !

well, most painless solution was to only copy over all visible folders
+ .mozilla, .gaim, .xchat2
i suggest not copying all since that kinda ****** up for me...

sage

---

### Post by bodhi.zazen on 2007-08-17
> **ProN00b said:**
> thats exactly what i been saying if you listen closely, 
"Go to System -> Administration -> Login Window

Under the security tab select auto login and user name (root)"
does not work !

oic, I missed that somehow, sorry

---

### Post by kerry_s on 2007-08-17
in gdmsetup there's also a box you need to check, that says "allow root login".

---

### Post by bodhi.zazen on 2007-08-18
> **kerry_s said:**
> in gdmsetup there's also a box you need to check, that says "allow root login".

Hi kerry. The "problem" is allowing root to **autologin** (and I thought you were going to come through with the answer :) )

---

### Post by djg5211 on 2007-08-30
Hello...

 Kerry (was it?) was correct. If you do not 'x' the allow local login then you
could not auto login with root because root is not ALLOWED to login by default.
Now, on to my two cents which i'm certain will piss someone off but here goes
anyway...

I am sitting here trying to figure out WHY 'LINUX' people are so 'FREAKED' about
logging in as 'ROOT'??? I could understand if everyone was a complete retard
but then think about this..... If they have enough knowledge about a computer
to install 'Linux ANYdisto' and they KNOW what they want to do with their own
system then why the big BRUHAHA? The ones who run public servers or have
networks in their place of business, i am somewhat inclined to believe, have
some notion as to the disasterous effects of such an action as auto logging as
ROOT since they have likely did some investigation as to the security built into
Linux which is probably why they chose it to begin with...

The reason i am even here on this forum was to find out if  login as root
was even possible at all (somehow) in Ubuntu as i was running PCLinuxOS
which allowed it and Mepis which had a workaround to allow it but if you
manually type in 'root' in that autologin deal in Ubuntu you get this:

''Autologin or timed login to the root account is forbidden.''

No (are you sure?), No (do you understand what you are doing?) just
plain old NO!!!! 

So, now that i got everyone pissed off i would still like to know if there is
a work around that doesn't entail 50 lines of code and chmods and stuff
like that. Must be a config file that can be edited as in Mepis or PCLOS.

Don't get me wrong.... I like Ubuntu probably best of the Linux distros that
i have tried and appreciate all of the long hours and effort invested in the
system by all of those dedicated individuals, but, not EVERYONE has to
''FORT KNOX'' their computer (like me) because i am the ONLY user of this
computer.

Okay now you can all respond with stuff like ''Quit whining and go to the 
Windows XP forum'' and stuff heh heh!!!

Dave

---

### Post by bodhi.zazen on 2007-08-30
:lolflag: djg5211

You are free to run how you like :)

We all have our personal preferences of course and I could go on and on about why running as rot is not for me ...

At any rate, you need to set a root password :

```
sudo passwd
```

Then enable root logins as kerry_s suggested.

The part I have not been able to do is enable root *autologin*

That will take some coding

---

### Post by Hopworks on 2007-10-16
I am also interested in autologin as root because...
When I log on as what I was hoping to be my main username, no matter what group I put that username in, when I try to do a lot of things in gnome, I get asked for my password, synaptic package manager, etc. When I login as root, that doesn't happen.

Since it appears that autologin as root isn't possible, or easily doable, how can I configure my main username so I don't get prompted for my password when I do administration type things. My main username is assigned to the administrator group, but apparently that doesn't help.

I'm interested in getting this working because I'm running TightVNC on my Windows XP laptop and it doesn't work if a user isn't logged into gnome. If I need to reboot my Linux machine, say via putty 'reboot', when it comes up, I have to go to that machine and log into gnome. Autologin works for my main username, but then I get the annoying password prompts when I do admin stuff. If I can turn off that hold-my-hand-securely 'feature', then I could copy over all my config stuff to that account and use it from now on.

I also want to thank all those that spend the time answering questions like this, and all that are responsible for Linux, Ubuntu, and all the wonderful free open-source answers to Windows. The more I use Linux Ubuntu Feisty, the more I love it. THANK YOU!

---

### Post by bodhi.zazen on 2007-10-16
You can either :

```
sudo -i
``` entering your password once for a root terminal.

Or

Edit /etc/sudoers to disable the need for a password.

See [man sudoers](http://www.gratisoft.us/sudo/man/sudoers.html)

---

### Post by Hopworks on 2007-10-16
> **bodhi.zazen said:**
> You can either :

```
sudo -i
``` entering your password once for a root terminal.

Or

Edit /etc/sudoers to disable the need for a password.

See [man sudoers](http://www.gratisoft.us/sudo/man/sudoers.html)Made a backup, then tried a few things and failed a few times, but now I got it.

One more thing, if you don't mind...

I'm curious as to why I didn't get the desired results when I added
%admin ALL=NOPASSWD: ALL
under the 
%admin ALL=(ALL) ALL
since my target user is a member of the admin group. Actually, I might have put it above that, and the order matters from what I read. Is that why it didn't work?

Thank you!

Hop

---

### Post by bodhi.zazen on 2007-10-16
Glad to hear you got it working. I am afraid I am not an expert on /etc/sudoers and usually have to hack my way through it by trial and error myself so I do not know the answer to your question.

---

### Post by Hopworks on 2007-10-16
> **bodhi.zazen said:**
> Glad to hear you got it working. I am afraid I am not an expert on /etc/sudoers and usually have to hack my way through it by trial and error myself so I do not know the answer to your question.No problem =)

When I get a few minutes later, I'll reverse that order and see if it works. It would be nice to make a special group that acts like I want it to (no password) and leave the admin alone as it should be.

Make one. wheel is a good choice.

---

### Post by Hopworks on 2007-10-16
> **aysiu said:**
> Moving from /root to /home/*username* and *chown*ing **should** work, but I wouldn't move everything, only the folders that matter...
Thank you. That piece of info about chown was invaluable to me, as were the folder names. I copied those folders over, but then couldn't login on that user. I read it again, and sure enough. But I never had to do that before, so more google. Then, the hidden folders didn't change ownership, more google. Then finally I had to chown the username folder itself. Now it works great!

So this thread fixed a real bugger for me, and I learned a lot today.

It's a little out of topic, but how would one script this process? I may want to do it again, and would like to run the script logged on as root, with a parameter for the source and destination username. I tried a few different things with a script and failed, mostly using CP to copy the folders over. I read the man on CP over and over, but I'm thinking maybe the destination folders were not there is why. I just assumed the folders would be created if they didn't exist. I don't see an option in CP for that.

I tried doing it on a single folder also, but it didn't work. ```
cp -r /root/.config/. /home/backup/root/.config
```

If someone could give me a reference for more in-depth reading on scripting the copying of hidden folders recursively, I would very much appreciate it.

Thanks again!
Hop

---

