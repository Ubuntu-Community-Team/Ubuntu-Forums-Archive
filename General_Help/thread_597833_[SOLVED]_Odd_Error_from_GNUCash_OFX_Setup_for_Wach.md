---
title: "[SOLVED] Odd Error from GNUCash OFX Setup for Wachovia Bank"
date: 2007-10-30
forum: General Help
---

### Post by troyer81 on 2007-10-30
Has anyone successfully connected to a Wachovia Bank Account using GNUCash/libaqbanking??

I've searched left and right, up and down, for any kind of answer, but I have been unsuccessful in my search.  I would not consider myself a Linux "newbie," but I'm not sure where to start in debugging this "error".  Anyway, here's the setup:

Ubuntu Gutsy 7.10
GNUCash 2.0.5
libaqbanking 2.2.3-4 (with associate OFX library)

When I setup my Wachovia Bank Account with the OFX information that I found here ([http://ofxblog.wordpress.com/?s=Wachovia](http://ofxblog.wordpress.com/?s=Wachovia)) and I click "Get Accounts," I get the following error (after entering my ID and password):

***OFX: General error (Invalid Product or Version. The Software Version you are attempting to connect with is not supported by your financial institution, please contact Customer Service for more information.)***

My first thought was that the Wachovia servers somehow block anything that comes across that doesn't specifically identify itself as "M$ Money" or "Quicken."  I don't think that's the case though, since MoneyDance seems to connect perfectly (and MoneyDance is not officially supported by Wachovia, either).  Is MoneyDance using a different library for the OFX transactions?  If so, why can't libaqbanking mimic the transaction format?

I would really like to start using GNUCash instead of rebooting into XP just to use M$ Money.  Can anyone out there at least point me in the next direction for debugging?

Thank you in advance,
Jon

---

### Post by troyer81 on 2008-02-22
Apparently I ended up talking to myself, but I did eventually find an answer after several months of searching and hopefully this post can help others

To my knowledge, Bank of America has the same issue as Wachovia and it has to do with the APPID and APPVER that libofx uses when creating its OFX transmission.  Anyway, the solution is to change the APPVER and/or APPID that libofx uses.  Unfortunately, until GNUCash upgrades to the new libofx package, we have to actually change the libofx sourcecode to change the APPID.  The good news is that you only have to recompile libofx, and not the entire "stack" of software up to GNUCash.  Anyway, here's the basic steps I used, just in case anyone else has the same problem:

First, download the source code and diff package for the version of libofx that's currently on your system (I found my version here: [https://launchpad.net/ubuntu/gutsy/+source/libofx/1:0.8.2-3ubuntu2](https://launchpad.net/ubuntu/gutsy/+source/libofx/1:0.8.2-3ubuntu2))

After unpacking the source and applying the diff/patch, open the appropriate source file of interest, lib/ofx_request.cpp

Find the APPID string (line 79) and change it to "Money" and change APPVER to "1700" to mimic the newest version of M$ Money.  There are other options, but those worked for me.  Save the file and recompile libofx (./configure --prefix=/usr && make && sudo make install, assuming you want to overwrite the existing libofx libraries)

At that point, you should just need to restart GNUCash and you're set!

I know that was a sketchy path to the answer, but hopefully it helps anyone else having similar problems.  If you have any questions, feel free to ask and I'll answer to the best of my ability.

Good luck!

P.S. I'm headed over to a forum for suggestions to create an Ubuntu package of libofx that applies a more recent APPID and APPVER to libofx....We'll see how that goes.

---

### Post by you-bunt on 2008-03-21
I can relate to the searching left and right, up and down.  I often feel I'm going in circles or nowhere.  I too don't consider myself a Ubuntu newbie, but often find the steps to get from 'here' to 'there' as daunting as attempting to climb Mt. Everest in the dark after 3 trips to a climbing wall.

I'm encouraged that you have found solutions to APPVER and/or APPID that libofx uses since we have both BoA and Wachovia accounts.

But I'm a couple of steps behind you, so can you offer any help?

My predicament:
Cutting through a whole lot of painful steps trying to upgrade from Dapper to Gutsy, here are key things that I think the forum instructions suggests I include.  I'm including since I'm not sure if they are relevant, but find that a slight oversight can cause great confusion.

Installed Gutsy from iso. onto a hard drive with no other linux on it.
Used Synaptic and:
got most Important Security updates [still getting some 'fail' connections with many rabbit trails trying to find another solution to one more issue I would not have expected... I stopped looking]
got Recommended updates

don't remember exact steps with Synaptic, but still with Gutsy repositories:
got gnucash and gnucash-common [2.0 something?]
got aqbanking16-qt-wizard & aqbanking-tool
After getting little headway and more searching, decided these versions may not have fixes for OFX issues that was a main quest to start using gnucash.

Used Synaptic and:
added repositories for Hardy main and universe repositories:
did get both the various gnucash and aqbanking packages, including dependencies.
For what I think are the 3 relevant packages Synaptic now shows:
aqbanking16-qt-wizard & aqbanking-tool 2.3.3-2
gnucash & gnucash-common                2.2.3-1ubuntu3
libofx3 & libofx4                                   1:0.8.2-3ubuntu2 & 1:0.9.2-2ubuntu1 

I then 'detached' the two indexes from Hardy repositories so as not to further confuse matters.

I then found that I cannot simply use gnucash and aqbanking it seems because of some 'liscensing incompatibilities'.  [Found in [http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian) which I got to from Setting up OFXDirectConnect in GnuCash 2 [http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2]](http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2])


This now brings me close to my concerns:
These were the most recent detailed instructions I can find and yet they refer to gnucash 2.0.1-3ubuntu3
With the Debian [I have gotten my brain to wrap around Debian and Ubuntu were kissing cousins] instructions shifting to Command Line Interface 'apt-get' and me not knowing interworkings of apt-get, I'm concerned that apt-get goes to 'index' of same packages that Synaptic now has [remember I detached back to just Gutsy and not Hardy packages from whence I had gotten latest gnucash/aqbanking/libofx], that things will get out of kilter.

I can see 3 possible main paths forward.  There may be more.
[LIST=1]
[*]Someone assure me of steps to keep apt-get in sync with packages I have and follow Debian wiki type step-by-step instructions
[*]Someone tell me steps to Backup from where I am and then steps go forward again
[*]Someone tell me there is a simpler way, preferably within GUI with these later versions PLEASE!
[/LIST]

Editorial: It sure would seem Gnucash could be a good attractant package to Linux for non-techy PC users.  Most non-techy users are not interested in climbing Mt. Everest - just install and use the software.  Thus, it sure would seem nice to have a something like a shell script to get through all the gathering system info., determining what package versions already exist, if any, getting appropriate latest packages with dependencies, installing and linking any existing data files, dealing with any configuring issues, etc.  But once again, what may seem simple, it may be more complicated than that.

---

