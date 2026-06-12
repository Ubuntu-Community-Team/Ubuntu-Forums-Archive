---
title: "[SOLVED] NEED help... Up dates wont work again"
date: 2007-09-01
forum: General Help
---

### Post by crazygun on 2007-09-01
okay here is my problem.... i just fixed my up data system last time and it was doing great. well one day i come home and it stops... working out of no where. and i forgot everything i had to do before... so i don't know what codes to used to fix it. I just wanted to know if any one knew what they were and can help me out. An other thing I am trying to put limewire on my computer and it work let me do that either... 



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

that is what the up date system is saying:-----^

and this is what the limewire is saying: 

Only one software management tool is allowed to run at the same time
Please close the other application e.g. 'Update Manager', ;aptitude' or 'synaptic' first 


and I did what it told me to do.... and it is still saying it. 
so if any one can help me that would be great!

---

### Post by sumguy231 on 2007-09-01
You need to go to a terminal and run 'sudo dpkg --configure -a' to fix the problem.

---

### Post by crazygun on 2007-09-01
okay i did that and now im getting this on my update system... 

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.



.....but i dont know how to use the Synaptic ..... now what?

---

### Post by Lord Illidan on 2007-09-01
Ok, type this in a terminal : sudo apt-get install -f.

And press Enter.

Now stop there. It should be asking you to press y/n. Don't do anything just copy and paste everything here, please.

---

### Post by crazygun on 2007-09-01
okay... i did what it said and now its not working at all....

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by crazygun on 2007-09-01
okay I did what you said and this is what im seeing now...


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by crazygun on 2007-09-02
Okay Now it wont let me do anything... So does anyone have any type of idea i can do...

all i need are the codes to work everything and i think ... maybe i can fix it.
this is the second time this has happen to me.

---

### Post by jazz452 on 2007-09-02
Same thing happened to me today cant install or fix anything just says E: The package limewire-basic needs to be reinstalled, but I can't find an archive for it.try to install manually and samething i always use frostwire with no probs just thought id hav ago with limewire works fine on gutsy but not on feisty. Synaptics doesnt work either

---

### Post by forestpixie on 2007-09-02
you might need to try with this - I had to use it when I ended up going round in from circles with this

```
sudo dpkg --remove --force-remove-reinstreq packagename
```

jazz452- you would need to replace name with limewire-basic _IF_ that's what you were trying install

crazygun - you need to know what's half done - you could try ```
sudo dpkg -C
```

---

### Post by jazz452 on 2007-09-02
j@j-desktop:~$ sudo dpkg --remove --force-remove-reinstreq limewire-basic 
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `limewire-basic' missing, assuming package has no files currently installed.
152511 files and directories currently installed.)
Removing limewire-basic ...
j@j-desktop:~$ 
worked like a charm thanks for that forestpixie

---

### Post by forestpixie on 2007-09-02
cool - hope all goes well for you - bear in mind that the command a bit of a monster so don't use it willy nilly - at least that's waht I read somewhere

why are you trying to use limewire - there are lots of torrent clients here - I use ktorrent , which is a kde app - tried deluge but don't get on with it. Have a look around :)

---

### Post by jazz452 on 2007-09-02
I used cause i was bored always use frostwire or ktorrent which both work well.But remember to disable chat in frostwire because it stops you typing in search bar strange.

---

### Post by crazygun on 2007-09-02
Thanks I will try that and I will tell yall if it works. I really hope so... cause i have a lot of updates to do.

---

### Post by crazygun on 2007-09-02
Okay now Im lost.... what are the codes i need to put into my terminal? 
 I am trying to fix my updates system still....


and yeah I am trying to put limewire on my computer... only cause thats the only system i know how to use. LOL I would just ask my older brother to fix my computer cause he is taking this type of crap in college, but he is like 2 hours away and I dont have the time to wait.

---

### Post by crazygun on 2007-09-02
Okay now i have a problem....

I put in 'sudo dpkg --configure -a'  and it asked me for my password like always. well i put that in and now its not doing anything in the terminal .... So now what do i do?

---

### Post by merlinus on 2007-09-02
Ummmm...  did you press Enter after typing in your password?

Just checking....

-merlin

---

### Post by crazygun on 2007-09-02
yeah... i did... and i dont know why it didn't do anything

here im going to try it again and see what it does...

---

### Post by crazygun on 2007-09-02
okay now this is what it's saying to me.. and you can see what i am going throw..


 Sorry, try again.
Password: 
sudo: dpkg--configure: command not found
anna@dell:~$ sudo dpkg --configure -a
anna@dell:~$ 


okay.,... yeah i put it in wrong the second time... then once i put it in the right way it didnt do anything... nothing... no even asked me for my password. Now tell me what do i do?

---

### Post by crazygun on 2007-09-02
okay... i just put in: sudo apt-get install -f

and that worked like a charm... but now im at this blue and gray page and its not letting me do anything...

---

### Post by crazygun on 2007-09-02
okay my update system was running now its saying this


Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.


Now what!?!?!?

---

### Post by merlinus on 2007-09-02
You might try

 sudo dpkg --configure -a

again.

-merlin

---

### Post by crazygun on 2007-09-02
okay i did what you said  but now read this....


anna@dell:~$ sudo dpkg --configure -a
Password:
dpkg: status database area is locked by another process 
anna@dell:~$ 


okay that is what Im looking at right now....
now you have to know i have two terminals open right now... the other one has the Blue screen on it and its talking about Configuring sun- java6-bin 
          (that one wont let me do anything else in it so i had to open the new one)

---

### Post by merlinus on 2007-09-02
That may be the problem.  Close the configuring java terminal, and then try the dpkg command again.

If that does not work, try rebooting.

-merlin

---

### Post by crazygun on 2007-09-02
yeah it didn't work... So i am going to re-start my computer and try this again.

---

### Post by merlinus on 2007-09-02
And then enter the commands again, starting wtih

sudo apt-get install -f  

and then

sudo dpkg --configure -a

-merlin

---

### Post by crazygun on 2007-09-03
okay i did everything you told me to do... but once again...

its not doing anything after i put in the: sudo dpkg --configure -a

nothing is happening once again.......... 

but my update system is running.... now im going to sit here and see if it goes all the way through... and see if it doesn't tell me there is an other error some where.

---

### Post by jazz452 on 2007-09-03
I think u need to finish installing java and accept the agreement press tab to move to the i accept.once you install you will be able to put the codes in to fix the other problems.Do not use limewire use frostwire just the same as limewire but works great on linux.You cannot use frost or lime till you install java if you try you will mess up your pc.

---

### Post by jazz452 on 2007-09-03
MY best advice would be to use automatix                                                                       ( [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Automatix2) )  to install java and frostwire all codecs and many  other great programs.Go to unofficial ubuntu to install automatix.Another good program is envy to install your graphics driver.Use the second method to install automatix. (Install Automatix using apt (alternate method)paste commands 1 line at a time and press enter after each line hope this helps.

---

### Post by Mini Me on 2007-09-03
I've been having similliar problems too Jazz452 after installing turboprint

I get the following message when trying to run synaptic package manager

"E: The package turboprint needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

I've tried to run the script "sudo dpkg --remove --force-remove-reinstreq turboprint" from terminal and got the following

"dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 94514 files and directories currently installed.)
Removing turboprint ...
/var/lib/dpkg/info/turboprint.prerm: line 3: /usr/share/turboprint/lib/uninstall-pre: No such file or directory
dpkg: error processing turboprint (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/turboprint.postinst: line 3: /usr/share/turboprint/lib/install-post: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 turboprint"

And Synaptic package manager still has the samer error.... any ideas guys...

Thanks

---

### Post by jazz452 on 2007-09-04
That sounds nasty cant really help hope someone else can.Backup your data.Being an idiot i would delete the file in /var/lib/dpkg/info/turboprint and try the commands again.But i dont mind reinstalling,probably better waiting for someone who knows what their talkin about.

---

### Post by Mini Me on 2007-09-04
OK Tried that (thanks) - It would not let me delete the files

"Cannot move "/var/lib/dpk...nt.conffiles" to the trash because you do not have permissions to change it or its parent folder."

Any other ideas?

---

### Post by jazz452 on 2007-09-05
If you log in as root you will be able to delete file.

---

### Post by Mini Me on 2007-09-05
Ok Time to sound really thick - how do you log in as root....

I always use the Sudo command in Terminal.....

Thanks

---

### Post by jazz452 on 2007-09-05
go to system, administration,click (users and groups) click root then properties .Under password enter a root password think it needs to 6 letters or more put the password in the confirmation box as well.then ok and close.Next go system adminisration (login window) choose security tab at top and under security tick allow local system admin log in then close.Now from the shut down menu choose log out then you will be able to log in as root.Username (root) password whatever you chose

---

### Post by Mini Me on 2007-09-05
Thanks all it worked....

Deleting the files from root then using the script "sudo dpkg --remove --force-remove-reinstreq packagename"

I an relax again now... and update...

---

### Post by jazz452 on 2007-09-06
Nice one,you can also set to login automatically from the administration (login in window) if ure as lazy as i am.

---

