---
title: "support for exchange active sync"
date: 2013-02-24
forum: General Help
---

### Post by Apollo8 on 2013-02-24
I am planning on installing the 64 bit version of the latest Ubuntu onto a ThinkPad X1 Carbon. I am very attached to my Outlook.com email address. Exchange Active Sync keeps my phone and all my computers synced up with contacts, email, calendar, etc... Is there any Linux email client that will support EAS either out of the box, or with some plugin or mod? Yes, I know I can still use the web site to access all of that with Ubuntu, but I really like using a dedicated email client rather than the web interface. Any help would be appreciated. Thanks.

---

### Post by dcstar on 2013-02-24
> **Apollo8 said:**
> 
.......
Is there any Linux email client that will support EAS either out of the box, or with some plugin or mod?
.......

No. I believe that Microsoft charge for software vendors to use their proprietary ActiveSync protocol so no non-commercial developer will touch it.

Evolution used to be able to access Exchange via a web or MAPI interface but I haven't seen anything about Outlook.com support yet.

---

### Post by Apollo8 on 2013-02-25
Disappointing, but not unexpected.
 
I have been researching products call Wine and Codeweavers. If I could install Outlook 2013, I could use that to get my email. Not sure if those work with Outlook 2013 though...

---

### Post by icejoe75 on 2013-04-30
I have the same issue ... the best solution I could get was using Thunderbird + Davmail on ubuntu 12.04. Davmail connects to your account using Activesync, Thunderbird connects to Davmail using IMAP+CalDav.

---

### Post by Arkoon on 2013-05-20
Do you know this plugin:


[https://mail.gnome.org/archives/evolution-list/2012-May/msg00149.html](https://mail.gnome.org/archives/evolution-list/2012-May/msg00149.html)


I tried several times to compile this module, you can add a function to Evolution activesync but I still exposed on a compilation error (libtool: link: only absolute run-paths are allowed)

Can you try ? (I run Ubuntu Precise 64bits)

---

### Post by purjuju on 2014-04-13
So, finnaly, what is the solution?

---

### Post by nate-moore on 2014-04-22
> **purjuju said:**
> So, finnaly, what is the solution?

Unfortunately, there's not really a 'good' solution. Davmail (davmail.sf.net) appears to be the most popular option. It functions as a middle-man between Microsoft, and your standards compliant email tool (Thunderbird, Evolution, etc)

There is an Exchange plugins for Evolution too, evolution-ews. Near as I can tell, all it does is email. It seems to be slower than Davmail as well. There are Exchange calendar sync tools available as Thunderbird plugins too. Again, performance and stability appears to be an issue

Davmail is not without its problems. It relies on the system tray for configuration, assuming you're a GUI focused individual. Starting with Ubuntu 13, System tray access has been problematical at best. TimeKiller came up with a work around, and set it in his PPA ([https://launchpad.net/~timekiller/+archive/unity-systrayfix](https://launchpad.net/~timekiller/+archive/unity-systrayfix)) but it does not include updated versions for 13.10 and 14.04.

I have a message out to him to see if he's got time, inclination, etc, to patch it.

You *can* configure Davmail manually by editing ~/.davmail.properties 

Ultimately, although difficult, I suggest Davmail.  Long term, I think Microsoft needs to move to a standards compliant system, but I suspect they never will.

---

### Post by Mark Phelps on 2014-04-22
>  If I could install Outlook 2013, I could use that to get my email. Not sure if those work with Outlook 2013 though...

Outlook 2013 will not work in Wine -- the rating for Office 2013 is Garbage -- meaning, it's not going to work in Wine no matter what you do.

---

### Post by katanacb on 2014-05-06
evolution (with the ews plugin) uses exchange web services (Hence the "ews") to connect to an exchange server.  Not sure if outlook.com uses that, but for our internal exchange server, I've been using it on various distributions for awhile now and it keeps your email, calendar, and even corporate address book in sync with exchange.  It's just like having an Outlook email client -- without having Outlook.

---

### Post by Apollo8 on 2014-05-17
Thunderbird with 14.04 allowed me to set up my Outlook.com account using IMAP. The net effect is that my email now syncs just like it does with my Windows 8 and BlackBerry devices. I am very pleased.

---

### Post by rolandruiken on 2014-05-29
I have also 14.04 - but thunderbird can not connect to the outlook server.  The server needs port 443, but this can i not choose under thunderbird.... What to do ?

---

### Post by brian_woods on 2014-05-29
Thunderbird is the best option for it .

---

### Post by slcpunk on 2014-06-06
> **rolandruiken said:**
> I have also 14.04 - but thunderbird can not connect to the outlook server.  The server needs port 443, but this can i not choose under thunderbird.... What to do ?

just change the port here?

[ATTACH=CONFIG]253792[/ATTACH]

Also ... I think there is a key difference in Exchange setups.  2010 can be setup with or without IMAP support and may be limited to EWS.  In those cases, I am not sure if you can get Exchange connections going.  ( I haven't ... but would love to hear how )

---

