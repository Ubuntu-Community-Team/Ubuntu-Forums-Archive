---
title: "Re:  Cant access desktop after updates....Pls help?"
date: 2016-01-11
forum: General Help
---

### Post by ndnboy on 2016-01-11
Good evening...... I am need of assistance after trying to install updates. I clicked on Update All on my desktop and once rebooted I can not log in past the welcome screen. I was able to type my password, screen would go black, then back to log in screen. I turned off and attempted today, now i can not even type password into login box.

Is there a way for me to access the PC, and reset?

I am not very knowledgeable on PCs in general and ubuntu. Its running on an OLD Dell 8400 that a go worker loaded it on a few years ago. It has worked fine but has been running VERY slow lately. Taught it may have been the updates it was saying it needed.

I do not know what version its running, if needed, how can i determine that with no login access?

Thank you

Hoping someone can lend some assistance, thx......

Here is the message I get after i attempt to login...

---

### Post by Bashing-om on 2016-01-15
ndnboy; Hello ..

Generally this condition we see is caused by a update breaking a proprietary graphic's driver.
Maybe also the problem is compounded by an improper shut down of the system.

To start this trouble shooting procedure, can you boot up to a terminal from the login screen ?
At the login screen what results with key combo clt+alt+F1 ?
Can you login here with user name and password - no response to the screen when password is entered ?

[INDENT][INDENT]the terminal;
[INDENT][INDENT][INDENT]our best friend[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-15
[COLOR=#000000]I cant get past login screen, gives me error posted, clt+alt+F1 gets me to the blank tty screen, Im able to type in Login name, enter, but when password comes up, [/COLOR][COLOR=#000000] no response to the screen when password is entered 

[/COLOR][COLOR=#000000]
Thx[/COLOR]

---

### Post by Bashing-om on 2016-01-15
ndnboy; Sorry

for that ambiguous instruction/remark  " - no response to the screen when password is entered ? " is the expected/normal behavior for security reasons.

Anyway .. you have a terminal at this crl+alt+F1 console interface ?

What results - to confirm that you have an active console interface - with terminal commands:
```

sudo apt update
sudo apt upgrade

```

Then we look at your system and see where the fault may lie .

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-15
Sorry, don't know how to access terminal to check listed codes...

---

### Post by Bashing-om on 2016-01-15
ndnboy; Hey ...

There are 2 ways to get to a "terminal" .

The easier is as advised in the above.
Boot to the GUI login screen, here instead of entering your password in the login box we want to activate a console interface, press the key combo ctl+alt+F1.

Do you now get a black screen with a prompt asking for your login credentials ?

[INDENT][INDENT]easy is better
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-15
I can get to the blank screen with login, that's where it accepts a login name but no password 

Thx

---

### Post by Bashing-om on 2016-01-15
ndnboyl Hummm ....


We are not communicating .
" that's where it accepts a login name but no password " <- does not tell me much or relate directly to what the problem might be .
I do expect one thing here, that you enter your password blindly and hit the enter key . 
You should now have an active terminal with a blinking underscore prompt awaiting your command:
as in my prompt :
> 
sysop@1404mini:~$ _


else, well you have a much more serious system problem than that of a graphics driver issue OR authorization to access "your" /home directory.

IF for real you can not activate this console, we attempt to activate a real terminal via the grub boot menu . A couple of ways here too that will meet our needs .

Or even the more drastic action of accessing your system from the live environment of a install medium.

Do not want to start chasing imaginary events, or make this any more difficult that it needs to be.

[INDENT][INDENT]more than one way
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-20
I enter password blindly (nothing types onto screen, stays blank), hit enter,  and get a Login incorrect message. 

I only see a blinking cursor next to another login request.....

Thx

I attempted to boot into command line with info I found.....added the comments listed of audio update/upgrade......now I'm at a little early that says.....


E: dpgk was interrupted,  you must manually run suddenly dpgk -- configure - a to correct the problem......

Has me at a blinking cursor :~$

---

### Post by Bashing-om on 2016-01-20
ndnboy; Ouch ...

Indicates deeper problem than a graphic's driver issue.
Are you 100% certain that the entered password is correct ?

Then let us see what results in booting to terminal from the grub boot menu.

Reboot the box, and as soon as the bios screen clears depress a shift key -> grub boot menu.
With the latest kernel selected to boot press the 'e' key for edit mode -> boot parameter screen.
In this screen arrow down to the line starting with linux, and across to quiet splash. replace "quiet splash" with the term "text" - with out the quotes. execute key combo ctl+x to continue the boot process to TTY1.

Can you log onto the system from this terminal ?

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-20
Yes, I'm able to login after TEXT comment....

It shows...

134 packages can be updated.
57 updates are security  updates.
Username@username-dimension -8400:~$

---

### Post by Bashing-om on 2016-01-20
ndnboy;Hey, outstanding ...

So likely a desktop config issue .

However 1st up is to get this system updated, get the vulnerabilities/security updates taken care of asap.
In this terminal run terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade

```

Advise of ANY errors. when updated we go back to seeing where the problem lies.

[INDENT][INDENT]progress made
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-20
After entering "sudo apt update"...it runs some code and gives me the....

E: dpgk was interrupted, you must manually run suddenly dpgk -- configure - a to correct the problem

.....Message....

---

### Post by Bashing-om on 2016-01-20
ndnboy; Yuk;

But not real surprised.
OK, do as the package manager advises And post back that output:
```

sudo dpkg --configure -a

```
If the system can not resolve on it's behalf we need to see that output in order to know what direction to take to help the system.
edit: note there are no spaces after '--' and '-' .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-20
Getting a command not found message

---

### Post by steeldriver on 2016-01-20
... I think that should be [SIZE=4][FONT=courier new]dp**kg**[/FONT][/SIZE] (pkg short for [SIZE=2]**p**ac**k**a**g**e[/SIZE])

---

### Post by Bashing-om on 2016-01-20
ndnboy; Well ..

check your spelling and syntax.
```

sudo dpkg --configure -a

```
a command is literal and must be letter, case, space, switch perfect to obtain the desired result.
I am aware that " dpkg --configure -a" has been depreciated, but in 14.04 should still be a valid command.
sudo space dpkg space --configure space -a return.
You will be asked for your password to execute a system command, input the password, see what the package manager does .


[INDENT][INDENT]a process of learning
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-20
Entered correctly,  system went through alot of what looks likes checks and updates....finally stopped with:

Errors were encountered while processing :
Linux -headers-generic-pae
Linux-generic
Linux -pae 
Username@username-dimension-8400:~$

---

### Post by Bashing-om on 2016-01-20
ndnboy; Ho Kay .....

We are making progress,, however ----
> 
Errors were encountered while processing :
Linux -headers-generic-pae
Linux-generic
Linux -pae 
Username@username-dimension-8400:~$

does not help a lot .. need to see the command and it's complete output so I see things in context.
I can imagine where we are going next ... but with the complete contextual output, better results are guaranteed .
```

sudo dpkg --configure -a | pastebinit

```
And pass the resulting link back here .

[INDENT][INDENT]slowly but surely
[INDENT][INDENT][INDENT]an inch at the time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-20
> **Bashing-om said:**
> ndnboy; Ho Kay .....

We are making progress,, however ----

does not help a lot .. need to see the command and it's complete output so I see things in context.
I can imagine where we are going next ... but with the complete contextual output, better results are guaranteed .
```

sudo dpkg --configure -a | pastebinit

```
And pass the resulting link back here .

[INDENT][INDENT]slowly but surely
[INDENT][INDENT][INDENT]an inch at the time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

Here is what I got...

---

### Post by Bashing-om on 2016-01-20
ndnboy; Ho Boy !

Not able to install pastebinit, sure makes things tedious.
However your pic did point out where the problem is .
So let's see what we can do to find a resolution.

Did you run out of disk space at some point and the linux kernel packages could not be installed ?
what returns:
```

df -h
df -i

```
to make sure we do operational headroom to start fixing.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]always fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-20
No issue with disk space....

commands entered show 

10%used when df -h

4% used when df -i

---

### Post by Bashing-om on 2016-01-20
ndnboy; K

Then let us look directly at the issue.
```

dpkg -l | grep linux- > kernel.txt

```
I do need to see that complete output ... maybe lots of kernels installed. We may have to get real inventive to relay a large amount of info. Such as: redirecting the outputs to a text file (kernel.txt), and attaching these text files in your thread . ( reply to thread  red button-> tools bar -> paperclip icon ) and "attach kernel.txt here in the thread is one way .


[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-21
I don't get anything after that last code entry....

Also, don't know how I can redirect text to you, can't access email from PC....can i take picture/video of screen and attach?

---

### Post by Bashing-om on 2016-01-21
ndnboy; Hey ....

Let's kick back and get the more comfortable with this our operating system BY choice.

In The command:
```

dpkg -l | grep linux- > kernel.txt

```
the 'l' is a lowercase letter "L" . -' l ' is for " list " -
OK ... familiarity.
Do " dpkg -l | grep linux-" and you get a long list of installed kernel packages. with the redirection (>)  
```

dpkg -l | grep linux- > kernel.txt

```
the output is to a text file ( kernel.txt) ; that info is now in that file:
so to see that is true. do : " ls -al kernel.txt " and in your terminal is the response similar to:
> 
-rw-rw-r-- 1 sysop sysop 2294 Jan 21 15:44 kernel.txt

Now that shows the file exist, and as well gives you several attributes about that file and the nature of the file . Here our interest is that the file exist .

So now to verify that the file has content, and you want to see what you are exposing to the world; do: 'cat kernel.txt'.

I really do have to see that entire file to give you advise on what the real situation is . Until such time as I "see", I can not know .

Now that we know the file exists with the info that I have requested,,, pass that file back here to the thread.
That is the job of the thread tools " paper clip " icon . Click on the paper clip icon in the thread took bar and follow the prompts to copy that file. (kernel.txt)

---------------------------------------------------
I do not do videos on this box as I have an old old ATI graphic's card that with videos will overheat and shut the system down .


[INDENT][INDENT]once you have done it
[INDENT][INDENT][INDENT]ain't nothing to it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-21
I can see a report after checking with cat.....how do I get it to you? I am on my phone, kernel.txt is on my desktop, which I can't  attach file from....

---

### Post by Bashing-om on 2016-01-21
ndnboy; Hey ....

Can not help with usage of the phone.

What is preventing you booting up the problematic box into ubunti to the TTY1 terminal ?
------------------------
EDIT: I can be dumber than a box of rocks !
Ouch !
You can not activate the GUI to get to a web browser !
I do not know how to " curl " back to the forum .

[INDENT][INDENT]lots of things
[INDENT][INDENT][INDENT]I do not want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-21
So nothing else to try, I have a picture of screen (but does not show all of kernel.txt).......

Don't know what the problematic box is...

Thx for help and trying to fix

---

### Post by Bashing-om on 2016-01-21
ndnboy; Ouch ...

See my edit to the last ... 

Hang loose, let's see who comes to our rescue to come  up with a means to transfer files .

[INDENT][INDENT]where there is a will
[INDENT][INDENT][INDENT]we make a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-01-24
ndnboy; New thought !

What results:
```

dpkg -l | grep linux- | nc termbin.com 9999

```
As with termbin we do not need to install anything .

Pass that resulting URL back here to the channel .

[INDENT][INDENT]more than one way !
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-24
Ok, thx......here you go:

[Http://termbin.com/paup](Http://termbin.com/paup)

---

### Post by Bashing-om on 2016-01-24
ndnboy; Hey !

The good thing is that it works !
However, not the output I had expected . Pleas check spelling and syntax and try again.
That 'l' is a lower case "L" . and a dash after "linux".

[INDENT][INDENT]way to go

[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-24
Corrected,  here u go....

[Http://termbin.com/y881](Http://termbin.com/y881)

---

### Post by Bashing-om on 2016-01-25
ndnboy; Nope,

Not that time .. I get a 404 ( file not found ) error when clicking your link.

try again . 

[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT](sky diving excepted )
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-25
Ok let's try.....

[Http://termbin.com/s5b1](Http://termbin.com/s5b1)

Thx

---

### Post by Bashing-om on 2016-01-25
ndnboy; Outstanding !

Now we are cooking .. and have something we can set our teeth into .

But I do have some questions :
1) We must know the currently booting kernel - WE MUST not mess with it>
Post back the return from terminal command:
```

uname -a

```
The '-a' switch because I want full disclosure on the booting kernel .

2) Why is " iU  linux-generic-pae " installed ( now partially ) as well as " iU  linux-generic " ? --- one or the other, but not both .

3) " version 3.13.0 on 32 bit x86 SMP " is a 32 bit install .. is your hardware that old that in today's world of 64 bit support 32 bit is used ??? Be aware, if 64 bit is the preferred architecture --- then the only option here is a complete fresh install of a 64 bit operating system. 
Do in terminal:
```

grep -w lm /proc/cpuinfo

```
If you see "lm" in red, it's 64 bits. Otherwise it's 32 bits. Also, do you see "pae" "sse" and "sse2' in the output ?

Here we are trying to determine which type of kernel we are going to support , generic-pae or the standard .

--------------------

The plot gets deeper and deeper ....
[INDENT][INDENT][INDENT]but we are not over our heads 
[/INDENT][/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-25
1) 3.13.0-48-generic #80-Ubuntu SUP Thu Mar 12 11:16:18 UTC 2015 i686 i686 i686 GNU/Linux

2)Don't know

3) No return from entered code

---

### Post by Bashing-om on 2016-01-25
ndnboy; Progress ....

Slowly ..

We now know you are booting the normal kernel - though a real old one !
mine:
```

sysop@1404mini:~$ uname -a
Linux 1404mini 3.13.0-76-generic #120-Ubuntu SMP Mon Jan 18 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
sysop@1404mini:~$ 

``` where I am booting the latest kernel on 64 bit hardware.

As to yours ... check again the syntax and spelling; as the command is valid:
```

sysop@1404mini:~$ grep -w lm /proc/cpuinfo
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_[color=red]lm[/color] cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv vmmcall
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl extd_apicid pni cx16 lahf_[color=red]lm[/color] cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv vmmcall
sysop@1404mini:~$

```
where I have a dual core processor.

So far look'n like we are going to do away with the pae kernel stuff .. maybe .

in order to make a valid decision
[INDENT][INDENT]got to have valid info
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-26
Getting same...nothing....

---

### Post by Bashing-om on 2016-01-26
ndnboy; Ouch !

The command you entered is correct ... seems we will have to re-think my process as look'n like this is in fact a 32 bit processor.
What returns:
```

sudo lshw | grep "description: CPU" -A 12 | grep width

```
It says clearly whether it's 64 or 32 bits (will take a little while to finish as the system looks over the hardware).

If this in a 32 bit processor, we want to keep the pae-generic kernel packages instead of the normal one.

Cranking over the sights
[INDENT][INDENT][INDENT]to look at this from a different perspective
[/INDENT][/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-26
Returns with a,

 width: 32 bits

---

### Post by Bashing-om on 2016-01-26
ndnboy; K .....

> 
width: 32 bits


[INDENT][INDENT](RE-)think'n - in progress
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-01-26
ndnboy; OK:

Here is what we have :
> 
iU  linux-generic-pae
iU  linux-headers-generic-pae 

iHR linux-headers-3.13.0-74-generic 

##where ALL the generic-pae kernels are marked 'rc'
rc  linux-image-3.2.0-29-generic-pae

decode: 'iU' == desired state for the 1st instance is (i)nstalled, and the 2nd instance status is (U)npacked ( but not unstalled);
---------- ' iHR' == desired state for the 1st instance is (i)nstalled, and the 2nd instance status is (H)alf-installed, (R)einstallation-required
'rc' == desired state for the 1st instance is (r)emoved, and the 2nd instance status is (c)onfig files remain.

I can see where there are no generic-pae kernels fully installed that the package manager is unhappy and we get that 'iU' status for the linux-generic-pae and linux-headers-generic-pae packages.

Let's take a gentle poke at the situation:
```

sudo apt install linux-image-3.2.0-40-generic-pae

```
see what the package manager reports . With the anticipation we may have to intervene  for the case of the meta packaging.

However, if the result of installing the -40-generic-pae kernel is positive, we will also re-install the 36,48, and 74 kernels.

[INDENT][INDENT]does not look so bleak now
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-27
Here you...thx

---

### Post by Bashing-om on 2016-01-27
ndnboy; Yuk ..

Not at all what I had expected the package manager to say .
Is this a chicken/egg situation ?

cogitating on a way to go forward here .

[INDENT][INDENT]where there is will there is a way
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-01-27
ndnboy;  OK;

A considered thought. What results:
```

sudo apt-get install --reinstall linux-generic linux-headers-generic  linux-headers-generic-pae linux-generic-pae linux-image-generic linux-image-generic-pae 

```
Post the complete outputs. see where we go from there.

[INDENT][INDENT]sometime I do wonder
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-27
Here u go....stuff looks like Chinese to me...thx again

---

### Post by Bashing-om on 2016-01-27
ndnboy; Well ..

verry difficult to work from a screen shot, Best I can see is there is a typo in " linux-headers-generic-pae ". There is a dash between each word.

Try again as:
```

sudo apt-get install --reinstall linux-headers-generic-pae

```

As there is no access to the screenshot when I am replying ( sheeshhh ) .. I can not verify that the others went well .. best I recall they did.

If this one runs clean .. show a new 'dpkg' list of the kernels:
```

dpkg -l | grep linux- | nc termbin.com 9999

```

let's see what we look like now .

[INDENT][INDENT]forward progress ??
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-27
[Http://termbin.com/4w10](Http://termbin.com/4w10)

---

### Post by Bashing-om on 2016-01-27
ndnboy; Hey !

404 error ( file not found) again on that last.

Try again.

[INDENT][INDENT]what can I say
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-28
Ran again..here you go

[Http://termbin.com/r3xo](Http://termbin.com/r3xo)

---

### Post by Bashing-om on 2016-01-28
ndnboy; Yuk ...

I see no change.

OK, in small steps; What results:
```

sudo apt-get install --reinstall linux-generic

```
does the package successfully install ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-28
Looks like something was "Done"....and other....

In the process of upgrading and installing items....

Done...

---

### Post by Bashing-om on 2016-01-28
ndnboy; Yeah ...

Some progress made ! .. But my next thought has now taken a side track .
Let's see now what results with taking the package manager's advise:
```

sudo apt-get -f install

```

still keeping in mind:
> 
iU  linux-generic-pae

see if the package manager will deal with this for us.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-31
It upgraded and installed some items...

---

### Post by Bashing-om on 2016-01-31
ndnboy; Well ...

Looking into my crystal ball. all I see is hazy. Can you help out a bit ?
> 
It upgraded and installed some items...

package manager in a happy state now ?
kernels ? .. can you now boot to the GUI ? When booting what happens ?
What is the kernel situation ( got to have a consistent kernel to build a driver to access the GUI) ?
```

dpkg -l | grep linux- | termbin.com 9999

```

work'n to get us
[INDENT][INDENT]a consistent kernel and a happy package manager
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-31
I rebooted and it took me right to the desktop, didnt need to login, able to access web, seems to still be working slow....but working!

Thanks so much for your help, is there anything else i should check to confirm all is good?

---

### Post by Bashing-om on 2016-01-31
ndnboy; Hey hey hey ...

Good things do happen ..

Checks:
1) What kernel is now set to boot:
```

ls -al /vmlinuz*
ls -al /initrd.img*
ls -al /boot

```

2) package manager happy :
```

sudo apt update
sudo apt upgrade

```

3) Is a driver loaded for the graphics :
```

sudo lshw -C display

```

maybe:
> 
anything else i should check to confirm all is good?

IF all the above returns positive ->

[INDENT][INDENT]we are good to go
[/INDENT][/INDENT]

---

### Post by ndnboy on 2016-01-31
1 shows a 3.13.0-76 generic 

2 said...reading package list....Done

3 looks like yes

Here are some screen shoots

---

### Post by Bashing-om on 2016-01-31
ndnboy; Uh Huh !

All looks good to me ...

I think you doed it .

If this matter is now concluded, and there are no further questions;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]it were a thing
[INDENT][INDENT][INDENT]but weren't no step for a stepper
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ndnboy on 2016-02-01
Thanks again, will do marking it solved.

Working slow but WORKING : )

Thx!

---

### Post by Bashing-om on 2016-02-01
ndnboy; Great.

If it is that slow open a new thread and let's find out the why.

[INDENT][INDENT]we can do that too
[/INDENT][/INDENT]

---

