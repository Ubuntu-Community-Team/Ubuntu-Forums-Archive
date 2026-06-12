---
title: "Dependency problem"
date: 2014-04-29
forum: General Help
---

### Post by Langstracht on 2014-04-29
I would like to install simplescreenrecorder and have tried to do so both via the command line and though the ubuntu software centre.

In both cases the install is aborted due to dependency issues.

For now at least these are:

> Depends: libasound2 (>= 1.0.23)
Depends: libavcodec53 (>= 4:0.8-1~) but it is not installable or libavcodec-extra-53 (>= 4:0.8-1~) but it is not installable
Depends: libavformat53 (>= 4:0.8-1~) but it is not installable or libavformat-extra-53 (>= 4:0.8-1~) but it is not installable
Depends: libavutil51 (>= 4:0.8-1~) but it is not installable or libavutil-extra-51 (>= 4:0.8-1~) but it is not installable
Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not installable or libjack-0.116 but it is not installable
Depends: libpulse0 (>= 1:0.99.1) but 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 is to be installed
Depends: libqtcore4 (>= 4:4.8.0) but 4:4.6.2-0ubuntu5.6 is to be installed
Depends: libswscale2 (>= 4:0.8-1~) but it is not installable or libswscale-extra-2 (>= 4:0.8-1~) but it is not installable
Recommends: libssr-glinject but it is not going to be installed

I have NO idea how to resolve this ... or if indeed it IS resolvable.

Any and all help muchly appreciated.

TIA

---

### Post by ian-weisser on 2014-04-29
> **Langstracht said:**
> Depends: libqtcore4 (>= 4:4.8.0) but 4:4.6.2-0ubuntu5.6 is to be installed

You seem to have installed an older PPA or other Non-Ubuntu repository to install software that conflicts with Ubuntu.
The simplest way to resolve is to uninstall the non-Ubuntu software, then disable the Non-Ubuntu repository or PPA.

Only software from the Ubuntu Repositories is supported by this forum. PPA and other Non-Ubuntu software are not supported by this community - contact those developers directly. 
Until you resolve the problem, your system will not receive security updates or any other updates.

---

### Post by Langstracht on 2014-04-29
Thank you for your reply.

Alas I am more confused than before.

If you mean I installed a PPA so as to get the (manual) installation of the programme, you are absolutely correct.  Although I have no idea whether it is "older" or not.

When the installation failed I removed the PPA.

On a whim I then went to the Ubuntu Software Centre and was pleased to find the programme there.

And started up the, subsequently aborted, install process.

You say I should uninstall the software ... but it did not install in the first place.

As indicated the PPA is not there.

I don't understand how my (temporary) manual installation of a PPA would cause/allow the Software Centre to add a programme.  And indeed, if that IS what it does, I would think that is a major bug.  Perhaps someone can comment/verify.

I was NOT looking for support for the software.  I was trying to add to my pea brain knowledge of how to "upgrade" library programmes.

What security or any other upgrades will I not be getting?  From ubuntu you mean?  And why would that be the case?

---

### Post by coffeecat on 2014-04-29
> **ian-weisser said:**
> Only software from the Ubuntu Repositories is supported by this forum. PPA and other Non-Ubuntu software are not supported by this community - contact those developers directly. 

@ian-weisser, where do you get that idea from? Of course forum members may try to help people with issues arising from trying to install or installing software from third-party sources. The main things that are not supported are anything to do with cracking, piracy, illegal activity, circumvention of terms of service and EULAs, and the like. If a person needs help with obscure software or obscure PPAs then there may be few members who have experience with that software but I would hope that members would help with whatever issues that may arise when using Ubuntu or one of the recognised flavours of Ubuntu. 

@Langstracht, to be clear with what happened, am I correct in thinking that the errors you posted in your first post are what you saw when you unsuccessfully tried to install simplescreenrecorder from a PPA, and that you have subsequently removed the PPA? If so perhaps you could tell us more about simplescreenrecorder - it is not a piece of software I have heard of - and which PPA you tried to use. Perhaps someone could help with the installation of simplescreenrecorder.

Also, are you getting any errors now when you try to install software from the official repositories? I am not clear whether you are still getting dependency errors.

---

### Post by ibjsb4 on 2014-04-29
> What security or any other upgrades will I not be getting? From ubuntu you mean? And why would that be the case?

Your package manager, whether it be apt-get or a gui, cannot resolve the problem for you and must be delt with manually.  So this will shut down the entire update process until repaired.  What happens when you try to update in terminal?

Have you checked your /etc/apt/sources.list.d?

---

### Post by ian-weisser on 2014-04-29
> **Langstracht said:**
> 
When the installation failed I removed the PPA.

On a whim I then went to the Ubuntu Software Centre and was pleased to find the programme there.


Okay, so you disabled the PPA. (good)
But the package you installed from the PPA is still installed on your system. (bad)
It's the package that causes the conflict. Uninstall the package.

To test if the problem is fixed, run Software Updater. If it runs successfully, the problem is resolved.
If Software Updater returns an error message, show us the complete output.

You won't get updates for *any* of your software until resolved.



> **coffeecat said:**
> @ian-weisser, where do you get that idea from? Of course forum members may try to help people with issues arising from trying to install or installing software from third-party sources. The main things that are not supported are anything to do with cracking, piracy, illegal activity, circumvention of terms of service and EULAs, and the like. If a person needs help with obscure software or obscure PPAs then there may be few members who have experience with that software but I would hope that members would help with whatever issues that may arise when using Ubuntu or one of the recognised flavours of Ubuntu. 

@coffeecat, Thank you. My apologies to Langstracht for misleading him on the purpose of the forums.

---

### Post by Langstracht on 2014-04-30
>  to be clear with what happened, am I correct in thinking that the errors you posted in your first post are what you saw when you unsuccessfully tried to install simplescreenrecorder from a PPA, and that you have subsequently removed the PPA? 

That is correct.  And those errors (I'm pretty sure) were replicated exactly when I tried to install from Ubuntu Software Center.

> If so perhaps you could tell us more about simplescreenrecorder - it is not a piece of software I have heard of - and which PPA you tried to use. Perhaps someone could help with the installation of simplescreenrecorder.

See:  [http://www.maartenbaert.be/simplescreenrecorder/](http://www.maartenbaert.be/simplescreenrecorder/)

> Also, are you getting any errors now when you try to install software from the official repositories? I am not clear whether you are still getting dependency errors.

I haven't tried to install anything "official" and what with this apparent problem with the Center offering the simplescreenrecorder installation I'm not sure how I would know it IS "official".

As I asked previously could someone check THEIR Software Center and see if simplescreenrecorder is there?  If so, then why won't it install.  If not, well I still don't know how to get rid of it.

> Your package manager, whether it be apt-get or a gui, cannot resolve the problem for you and must be delt with manually. So this will shut down the entire update process until repaired. What happens when you try to update in terminal?

Sorry I don't know how to answer this.  It "runs", shows a couple of errors, many "Get"s and "Hit"s.  Assuming there is no name change, there would appear to be no sign of either the simplescreenrecorder software or the above url.

> Have you checked your /etc/apt/sources.list.d?

I now have.  There are 2 entries relating to screen recorder.  I take it they should NOT be there.  If so, am I safe in just deleting them?  Or will that just create more problems.

Are the entries the reason they show up in Ubuntu Software Center?

> Okay, so you disabled the PPA. (good)
But the package you installed from the PPA is still installed on your system. (bad)
It's the package that causes the conflict. Uninstall the package.

But as I explained the installation failed ... and so I have to believe the package is not uninstallable ...

> To test if the problem is fixed, run Software Updater. If it runs successfully, the problem is resolved.
If Software Updater returns an error message, show us the complete output.

Update Manager - as I think you suspected returns an error:  see attached.

One last point/question that I tried to make before.  I was under the impression that the Software Center was populated with software that "Ubuntu" knew worked/approved etc.  Is that not the case?

---

### Post by ian-weisser on 2014-04-30
I think we have insufficient data here. The problem you describe might be caused by the SimpleScreenRecorder PPA package...or another previously-installed PPA package...or something else.

While we help you fix this problem, please use Terminal instead of Software Center, and please post the complete output to everything you try.
The exact terminal error messages, and the order in which the messages occur, are *very* helpful.

Please open a terminal and show us the *complete* output of
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by mc4man on 2014-04-30
What release of Ubuntu are you using?, the package versions reported for libqtcore4 & libpulse0 seem to indicate 10.04 (Lucid

---

### Post by Langstracht on 2014-04-30
> Please open a terminal and show us the *complete* output

Output is attached.

> What release of Ubuntu are you using?

10.04 as you surmised.

---

### Post by ian-weisser on 2014-04-30
Well, that's the "update" half of what we need.
The other half, "upgrade" will tell us a lot more.

Looks like you are using a lot of PPA software. That's rare in a server, so I surmise you are likely using 10.04 Desktop.
10.04 Desktop is past end-of-life and no longer supported.

You are also hitting PPAs that no longer exist. You should delete those. If you are no longer using that software, you should uninstall it.

---

### Post by Ubi_one_2014 on 2014-04-30
cd /etc/apt/sources.list.d

ls[enter]

pls post output here

---

### Post by Langstracht on 2014-05-01
> Well, that's the "update" half of what we need.
The other half, "upgrade" will tell us a lot more.

The results I attached were the result of the command:

```
sudo apt-get update && sudo apt-get upgrade
```

you asked me to use.

Running (just):

```
sudo apt-get upgrade
```

results in what is in the new attachment.  I did NOT continue the process.

> Looks like you are using a lot of PPA software. That's rare in a server, so I surmise you are likely using 10.04 Desktop.
10.04 Desktop is past end-of-life and no longer supported.

Yes, I did indicate (confess) I was using 10.04.  I'm somewhat aware of the limitations of that.

> You are also hitting PPAs that no longer exist. You should delete those. If you are no longer using that software, you should uninstall it.

Were I able to identify them it would behoove me to delete and uninstall ...

---

### Post by ian-weisser on 2014-05-01
1) Do 'sudo apt-get upgrade' again, but hit 'y' instead of 'n'.
If it works, then your package manager is working, and your reason for posting here is fixed. (Seems unlikely to me - we haven't done anything to fix the problem yet)

If it doesn't work,we really need to see the entire stream of error messages. 

2) Please show us your sources directory list (command: **ls /etc/apt/sources.list.d/ **) Ubi-one is right to ask in that direction.
3) Please show us your sources list (command**: ****cat /etc/apt/sources.list **)

> W: Failed to fetch [http://**ppa.launchpad.net/alex-p/notesalexp](http://**ppa.launchpad.net/alex-p/notesalexp)**/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found
W: Failed to fetch [http://**ppa.launchpad.net/sevenmachines/flash](http://**ppa.launchpad.net/sevenmachines/flash)**/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

4) You should delete both of those long-gone PPAs.

---

### Post by Langstracht on 2014-05-01
> cd /etc/apt/sources.list.d

ls[enter]

pls post output here

```
alex-p-notesalexp-lucid.list
alex-p-notesalexp-lucid.list.save
cinelerra-ppa-ppa-lucid.list
cinelerra-ppa-ppa-lucid.list.save
getdeb.list
getdeb.list.save
google-chrome.list
google-chrome.list.save
google-earth.list
google-earth.list.save
google-talkplugin.list
google-talkplugin.list.save
gwibber-daily-ppa-lucid.list
gwibber-daily-ppa-lucid.list.save
jon-hedgerows-get-iplayer-lucid.list
jon-hedgerows-get-iplayer-lucid.list.save
maarten-baert-simplescreenrecorder-lucid.list
maarten-baert-simplescreenrecorder-lucid.list.save
sevenmachines-flash-lucid.list
sevenmachines-flash-lucid.list.save
shiki-mediainfo-lucid.list
shiki-mediainfo-lucid.list.save
stebbins-handbrake-releases-lucid.list
stebbins-handbrake-releases-lucid.list.save
```

---

### Post by Langstracht on 2014-05-01
> 1) Do 'sudo apt-get upgrade' again, but hit 'y' instead of 'n'.
If it works, then your package manager is working, and your reason for posting here is fixed. (Seems unlikely to me - we haven't done anything to fix the problem yet)

If it doesn't work,we really need to see the entire stream of error messages. 

Not sure what "works" means.   I was totally unprepared for the output - which must have been many hundreds of lines (guess this is something I should have done previously and often huh?) but it seemed to "end" normally.  Returning to the prompt and no "abend".

As it flew by the only "errors" I saw were "already exists" and "error" against /etc/ssl/certs.  But other than that ... clean ... but long.

> 2) Please show us your sources directory list (command: ls /etc/apt/sources.list.d/ ) Ubi-one is right to ask in that direction.

Attached to previous post.

> 3) Please show us your sources list (command: cat /etc/apt/sources.list )

Attached to this post.

---

### Post by ian-weisser on 2014-05-01
> **Langstracht said:**
> Not sure what "works" means.   I was totally unprepared for the output - which must have been many hundreds of lines (guess this is something I should have done previously and often huh?) but it seemed to "end" normally.  Returning to the prompt and no "abend".

As it flew by the only "errors" I saw were "already exists" and "error" against /etc/ssl/certs.  But other than that ... clean ... but long.

If it finished without any errors, then your package manager must be working properly. Congratulations.

Try installing SimpleScreenRecorder again. If the install fails again, then SimpleScreenRecorder is indeed incompatible with some existing package on your system. You should let the SimpleScreenRecorder developer know that.

If you _really_ want to install SimpleScreenRecorder despite the conflict, then you must wander the paths of dependencies until you discover the offending PPA package. If you want to go down that not-easy path, let us know and I'll show you the tedious process.

---

### Post by SeijiSensei on 2014-05-01
> ```
alex-p-notesalexp-lucid.list
alex-p-notesalexp-lucid.list.save
cinelerra-ppa-ppa-lucid.list
cinelerra-ppa-ppa-lucid.list.save
etc,

```

That seems like a strange list of packages to be installed on a server.

---

### Post by Langstracht on 2014-05-01
I appreciate all the help given here ... and I'm very relieved to hear that (I think) I don't have a "general" problem after all.

That said I still have some loose ends,

If it performs anything like as advertised, yes I would very much like to install simplescreenrecorder. Turns out it is (still) "available" on Ubuntu Software Center.  

As I have asked a couple of times before, "is this normal?" (as in, is it in other people's USCs) or is this another problem that I DO have.

So, if I am to (try to) install the programme again, do I use the Software Center or not?

If the programme should not be there, is the cause the entries in sources.list.d?  And if so can/should I just delete them or is something different required.

Similarly are there any issues with what's in /etc/apt/sources.list?

There have been a couple of mentions about a "server".  10.04 is running on an acer laptop.  there is no server involved as far as I know.

---

### Post by ian-weisser on 2014-05-01
If you were using a supported version of Ubuntu, my advice would be to ALWAYS try the Ubuntu Repositories (Software Center) first. Some PPAs are great, but some break your system, and you have no way to tell in advance which is which, and PPAs are *not* supported by the Ubuntu community. PPAs are appropriate if you're testing software and actually filing bugs, or if you _really_ need some new feature in the latest version, or if you want the latest version and are willing to accept the risk. You accepted the risk.

But you're *not* using a supported version of Ubuntu. My advice is to use a supported version of Ubuntu. Like 14.04, which is supported until 2019.

About /etc/apt/sources.list and sources.list.d: 
Applications *appear *in Software Center when the application is in a Repository/PPA that is in those lists. Applications don't *disappear* from SC due to a conflict or setting.
The only way to make an application *disappear* from Software Center is to remove the Repository/PPA.
Two applications that conflict will both show in Software Center - the conflict only matters when you try to install both.

---

### Post by Ubi_one_2014 on 2014-05-01
as root:

cd /etc/apt/sources.list.d

rm alex-p-notesalexp-lucid.list alex-p-notesalexp-lucid.list.save sevenmachines-flash-lucid.list sevenmachines-flash-lucid.list.save[enter]
apt-get update && apt-get dist-upgrade [enter]

if everything works, rm *.list.save[enter]


there is no specific need to use software centre to install software, actually... i never use it to install software
a simple apt-get install [package] will do it

or else, with downloaded packages.. dpkg -i [package], and mostly followed by apt-get -f install to resolve dependencies

---

### Post by Langstracht on 2014-05-01
> But you're not using a supported version of Ubuntu. My advice is to use a supported version of Ubuntu. Like 14.04, which is supported until 2019.

I was advised it was likely that, given the changes in graphics in 12.04, my machine would not work.  So I stayed with 10.04.  I imagine 14.04 would also pose a problem.

> About /etc/apt/sources.list and sources.list.d: 
Applications appear in Software Center when the application is in a Repository/PPA that is in those lists. Applications don't disappear from SC due to a conflict or setting.

O.k. just to make sure I understand this - the reason simplescreenrecorder appears in the USC is that "I" have added it,  

As I said in an earlier post, if this is true, surely that is a problem.  It is my impression that many folks (including me) believe the stuff in USC is "approved" and "works".

> The only way to make an application disappear from Software Center is to remove the Repository/PPA.

Alas, as I think I said in my first (and subsequent) post(s), I removed the PPA right after the manual installation aborted.  So, present the PPA is NOT there ,,, and still the program shows in USC.

So again, do I need to get: 

```
maarten-baert-simplescreenrecorder-lucid.list
maarten-baert-simplescreenrecorder-lucid.list.save
```

removed from sources.list.d?  And, if so, how do I do that?

---

### Post by Ubi_one_2014 on 2014-05-01
pls follow up my recommendations

---

### Post by Langstracht on 2014-05-01
I had not seen your post prior to submitting mine.  Sorry about that.

> as root:

cd /etc/apt/sources.list.d

rm alex-p-notesalexp-lucid.list alex-p-notesalexp-lucid.list.save sevenmachines-flash-lucid.list sevenmachines-flash-lucid.list.save[enter]
apt-get update && apt-get dist-upgrade [enter]

if everything works, rm *.list.save[enter]

O.K., without understanding why, I have done your bidding.

This all started with maarten-baert.  Why did I not remove it/them too?

Does your instructions mean that *.list.save should never be in the directory?  If so why/how do they get created?  And should one be continually on the look out for them and remove them?

And what has this actually done?  Are the various PPA entries (/etc/apt/sources.list, sources.list.d, Administration>Software Sources) independent of each other?

> there is no specific need to use software centre to install software, actually... i never use it to install software
a simple apt-get install [package] will do it

I wasn't trying to suggest there was a need ... I was, as I have repeatedly said, under the impression that an installation from there was supposed to be "safe" and worked.  Isn't that the case?

> or else, with downloaded packages.. dpkg -i [package], and mostly followed by apt-get -f install to resolve dependencies

So, given my wish to snag simplescreenrecorder, what do I do?  Software Center (it IS still there even after all of this)?  apt-get?  Or dpkg -i?

---

### Post by Ubi_one_2014 on 2014-05-01
i am willing to answer all your questions, but i want to be focused on your dependency problem

are you still dealling with errors upon:
apt-get update && apt-get dist-upgrade[enter]

?
from my point of view the dead repo's should be removed

---

### Post by Langstracht on 2014-05-01
> are you still dealling with errors upon:
apt-get update && apt-get dist-upgrade[enter]

Well, without trying to split hairs, I never had a problem with update and upgrade.

The errors showed as a result of the aborted attempts at trying to install simplescreenrecorder which reported dependency issues.

> from my point of view the dead repo's should be removed

No argument from here.  But ... haven't I already done that?

---

### Post by ian-weisser on 2014-05-01
> **Langstracht said:**
> I was advised it was likely that, given the changes in graphics in 12.04, my machine would not work.  So I stayed with 10.04.  I imagine 14.04 would also pose a problem.

Perhaps. It's easy enough to test with a LiveUSB.
Since 10.04 desktop is beyond end-of-lfe and unsupported, you are certainly at higher risk of compromise from many known exploits.
So do be sure to do regular data backups, and don't be surprised if you get contacted by your ISP or law enforcement when they discover that your compromised machine is doing bad stuff.


> **Langstracht said:**
>  O.k. just to make sure I understand this - the reason simplescreenrecorder appears in the USC is that "I" have added it,  

As I said in an earlier post, if this is true, surely that is a problem.  It is my impression that many folks (including me) believe the stuff in USC is "approved" and "works".

Alas, as I think I said in my first (and subsequent) post(s), I removed  the PPA right after the manual installation aborted.  So, present the  PPA is NOT there ,,, and still the program shows in USC.

Only software in the Ubuntu Repositories is "approved" and "works." Not PPAs. Not anything else. I think you can understand why PPA and other non-Ubuntu developers won't highlight that. That's why Ubuntu deliberately makes it *harder* to add PPAs than one-click, or including in the install image.

The reason SimpleScreenRecorder appeared in Software Center is because you added the PPA. That action added all SimpleScreenRecorder's packages to the dpkg database. SimpleScreenRecorder should continue to appear in Software Center until you have _both_ 1) disabled the PPA, and 2) Deleted the package from /var/cache/apt/archives .


> **Langstracht said:**
> Does your instructions mean that *.list.save should never be in the directory?  If so why/how do they get created?  And should one be continually on the look out for them and remove them?

Those are backup files. You can delete them if you wish.


> **Langstracht said:**
> And what has this actually done?  Are the various PPA entries (/etc/apt/sources.list, sources.list.d, Administration>Software Sources) independent of each other?

/etc/apt/sources.list and /etc/apt/sources.list.d are independent. Software Sources, and all package managers, use both. sources.list has all Ubuntu repositories at install, including the 'main' repo of system-critical packages. sources.list.d includes all non-Ubuntu repositories, is much easier for your system to edit, and lowers the risk of accidental corruption to sources.list.


> **Langstracht said:**
> So, given my wish to snag simplescreenrecorder, what do I do?  Software Center (it IS still there even after all of this)?  apt-get?  Or dpkg -i?

Software Center and apt-get (and Synaptic and others) are essentially just different ways of telling dpkg to install the package.
dpkg probably won't do it. You already know why - Something you already have installed conflicts with it.
Go ahead and try. Maybe it will work this time.

In order to install SimpleScreenRecorder you must either deconflict the problem, or install from source instead of a package.

---

