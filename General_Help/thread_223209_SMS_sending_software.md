---
title: "SMS sending software"
date: 2006-07-26
forum: General Help
---

### Post by Bou on 2006-07-26
Hi, I'd like to know if there's any good, reliable SMS sending program for Ubuntu. Thanks a lot in advance.

---

### Post by JerMe on 2006-07-26
Not sure, but have you seen this?
[http://www.google.com/sendtophone](http://www.google.com/sendtophone)

---

### Post by DeadEyes on 2006-07-26
Send to Phone appears to only work in the US. Have you tried your providers website, I know mine allows me to send text messages for free once I register with them.

---

### Post by loell on 2006-07-26
there is [chikka]("http://www.chikka.com")
that work on selected countries and providers
it has a java applet version

---

### Post by Bou on 2006-07-26
I was mainly interested in a gtk program... not really for using it (I send few messages) but rather for showing it off to friends who do send them.

So I take it there's nothing like that? Oh well... :(

---

### Post by loell on 2006-07-26
i'd wish their is one too..

---

### Post by GTroy on 2006-09-10
I had trouble installing it, but there's a sms app calles smash

---

### Post by jr.gotti on 2006-09-10
Can't you do this in Gaim? Just "add new buddy" and put in +1XXXXXXXXXX as the screename...

Works for me...

---

### Post by wieman01 on 2006-11-11
No sure if you guys still looking for a solution by I am using Kopete together with "smssend". Fairly easy to configure...
> sudo apt-get install kopete smssend

---

### Post by xmastree on 2006-11-11
> **pixelPOET said:**
> Can't you do this in Gaim? Just "add new buddy" and put in +1XXXXXXXXXX as the screename...

Works for me...

Didn't work for me though... :( 
What protocol are you using for the account to which you add the buddy's mobile number?
I tried with Yahoo, but I couldn't add it.

---

### Post by loell on 2006-11-11
it surely does not.

---

### Post by andybleaden on 2006-11-14
> **wieman01 said:**
> No sure if you guys still looking for a solution by I am using Kopete together with "smssend". Fairly easy to configure...
Hi thanks for that. Downloaded it but as linux newbie got stuck as I tried to install it and then got very lost. I assume I must use adept manager to look for it but it ain't there. I tried to ensure its installed but keep getting stuck....any advice would be most grateful . I know it is on the pc and found all the folders with it on. Either pm me or icq 277487048 with any advice or reply here if you can

Many thanks

Andy

---

### Post by wieman01 on 2006-11-14
> **andybleaden said:**
> Hi thanks for that. Downloaded it but as linux newbie got stuck as I tried to install it and then got very lost. I assume I must use adept manager to look for it but it ain't there. I tried to ensure its installed but keep getting stuck....any advice would be most grateful . I know it is on the pc and found all the folders with it on. Either pm me or icq 277487048 with any advice or reply here if you can.
Open source-list from command line:
> sudo gedit /etc/apt/sources.list
Check that it has this line (for **Dapper**):
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) **[COLOR="Red"]dapper[/COLOR]** universe multiverse
Or for **Edgy**:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) **[COLOR="Red"]edgy[/COLOR]** universe multiverse
Once you have added it, run these two lines from command line:
> sudo apt-get install smssend
sudo apt-get install kopete
You should now have an option in Kopete to configure SMS protocols of various service providers: **Settings->Configure->New->SMS**

See screenshot for details...

---

### Post by andybleaden on 2006-11-14
Great , thanks for taking the time to do that 

Got this on the konsole

andy@andy-desktop:~$ sudo gedit /etc/apt/sources.list
Password:
sudo: gedit: command not found
andy@andy-desktop:~$ deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
bash: deb: command not found
andy@andy-desktop:~$ sudo gedit/etc/apt/sources.list
sudo: gedit/etc/apt/sources.list: command not found
andy@andy-desktop:~$ sudo apt-get install smssend
Reading package lists... Done
Building dependency tree... Done
smssend is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


So I take it it is installed but the sms thing ain't there with kopete. I will try an update kepote...hmmm. Perhaps it needs an update

Will get back to you 

Again thanks for your help

---

### Post by andybleaden on 2006-11-14
nah had a look...not there and kopete is updated.hmmmm

the first command you suggested came up with
sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
That may not help.......any ideas?

---

### Post by xmastree on 2006-11-14
You using kde? gedit is the default gnome text editor. Try nano instead.

---

### Post by andybleaden on 2006-11-14
ok tried that and got 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
??????

---

### Post by andybleaden on 2006-11-14
in fact it ain't in my list of programmes anywhere using adept.I can update it but I cannot see it

---

### Post by xmastree on 2006-11-14
> **wieman01 said:**
> Check that it has this line (for **Dapper**):
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse


> **andybleaden said:**
> ok tried that and got 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

[COLOR="Red"]**deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe multiverse**[/COLOR]


Add the line in red to the end of the file.
then run:
[B]sudo apt-get update
sudo apt-get install smssend
sudo apt-get install kopete
[/B]
that ought to do it.

---

### Post by wieman01 on 2006-11-14
> **xmastree said:**
> Add the line in red to the end of the file.
then run:
[B]sudo apt-get update
sudo apt-get install smssend
sudo apt-get install kopete
[/B]
that ought to do it.
Yes, sorry I went offline. Forgot to mention that you need to run an update after changing the source-list. You can refresh the repositories also using Adept.

One thing which will make life easier for all of us: Mention you distribution in your user options so that it shows when others read your posts. It avoids a lot of trouble, taking "gedit" as an example. :-)

---

### Post by andybleaden on 2006-11-15
will do and thanks once again for all of your contributions....will try again tonight as I am at work at the moment and on windoze

thanks 

Andy

---

### Post by andybleaden on 2006-11-17
Well I have tried and tried but maybe need more localised help with this hmmm

I did the nano thing and got this
# Multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# Multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security multiverse

# extra packages from kubuntu.org
deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) dapper main
  

tried to input sudo apt-get update     etc

and nothing happens . 

Will need to speak to local matey or someone over IM to talk me through this as I am lost. Many thanks for help so far though





Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg [189B]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get: 4 [http://kubuntu.org](http://kubuntu.org) dapper Release.gpg [191B]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://kubuntu.org](http://kubuntu.org) dapper Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Sources
Hit [http://kubuntu.org](http://kubuntu.org) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 5B in 0s (6B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
andy@andy-desktop:~$ deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe multiverse
bash: deb: command not found
andy@andy-desktop:~$
andy@andy-desktop:~$ deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe multiverse
bash: deb: command not found
andy@andy-desktop:~$ deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
bash: deb: command not found
andy@andy-desktop:~$ deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper multiverse
bash: deb-src: command not found
andy@andy-desktop:~$

---

### Post by wieman01 on 2006-11-17
Close Synaptic while you're running "apt-get".

---

### Post by chocbar31 on 2006-11-17
Here is a good resource for it. Just in case you're still looking.

[http://tuxmobil.org/phones_linux_sms.html]("http://tuxmobil.org/phones_linux_sms.html")

---

### Post by andybleaden on 2006-11-20
had a look at that also ....cheers

Andy

---

### Post by ofir_k on 2006-11-20
Hello,

I installed smssend but I still can't see SMS in the "Add Account Wizard".

There is a reason why?

Regards,
Ofir

P.S
I have Ubuntu Edgy

---

### Post by wieman01 on 2006-11-20
> **ofir_k said:**
> Hello,

I installed smssend but I still can't see SMS in the "Add Account Wizard".

There is a reason why?
What client software are you using? AIM? Kopete?

---

### Post by ofir_k on 2006-11-21
I'm using Kopete...

And I live outside the US.... I live in Isreal

---

### Post by wieman01 on 2006-11-21
ofir_k:

Same here, I live without the US but don't seem to have any problems. Have you installed Kopete & sendsms via Synpatic?

---

### Post by loell on 2006-11-21
where can i register an account for smssend , is it free?

---

### Post by wieman01 on 2006-11-21
Loell:

This is not the way it works actually. There are public SMS providers that let you send a certain amount of text messages per month; certain email providers offer that as well (so does mine... but it's a German website). So check it out on the web.

Kopete offers you a number of default configurations for various SMS providers. Perhaps simply pick on of them. They are mostly free.

---

### Post by loell on 2006-11-21
when i installed kopete and smssend in ubuntu/gnome , it doesn't show in kopete settings like the one in the screenshot :(

i can live with the smssend cli, but i don't know the provider name

---

### Post by loell on 2006-11-24
can someone post the list of free providers in kopete sms?
thanks ;)

---

### Post by jackhynes on 2006-12-02
I have the same problem as loell -- the SMS option doesn't show up in the New Account menu. I had Kopete installed before smssend but that wouldn't make any difference would it?

---

### Post by wieman01 on 2006-12-02
> **jackhynes said:**
> I have the same problem as loell -- the SMS option doesn't show up in the New Account menu. I had Kopete installed before smssend but that wouldn't make any difference would it?
Which version of Kopete are you using?

---

### Post by bofphile on 2006-12-04
> **wieman01 said:**
> Which version of Kopete are you using?

I have the same problem and I'm using Kopete 0.12.3 (Kubuntu Edgy).

---

### Post by wieman01 on 2006-12-04
Ok, guys. I am following this thread. Try to find more information tonight. Will get back to you.

---

### Post by wieman01 on 2006-12-05
This is odd... I am using verion 0.11.1 with smssend v3.4-2. I have no idea what the difference is but this is basically all I have installed. Then I go to "Configure" add a New account. That's it. 

Sorry I cannot help you guys. I have checked everywhere on the web, but I have found no hints at all. Kopete's documentation is insufficient in that the section on "Kopete SMS" is empty:

[http://wiki.kde.org/tiki-index.php?page=Kopete+SMS]("http://wiki.kde.org/tiki-index.php?page=Kopete+SMS")

---

### Post by bofphile on 2006-12-05
Maybe in the next version this problem will be solved.
Thanks for your help. ;)

---

### Post by elajth on 2006-12-23
I was fiddling around with kopete and smssend but couldn't either get the list of providers. So i tested installing smssend. And it worked:

sudo aptitude install smssend

yu'll also need to have the smssend prefix to /usr

Good luck!

Elajth

---

