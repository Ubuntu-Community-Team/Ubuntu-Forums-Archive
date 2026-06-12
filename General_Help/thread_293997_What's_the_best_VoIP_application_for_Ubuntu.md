---
title: "What's the best VoIP application for Ubuntu?"
date: 2006-11-06
forum: General Help
---

### Post by rozojc on 2006-11-06
Hi,
I have a question regarding VoIP. Under Windows I usually ran skype, which I also used under linux. Thing is that lately Skype decided not to accept credit card payments from credit cards issued in several countries (including mine), so I had to change my voip application of choice. Under Windows I tried Yahoo Messenger (which also offers long distance calls at cheap prices), but the Unix version of Yahoo messenger is WAY behind the windows one, so I can't make calls...

Besides skype, what is the best program, also available under linux and compatible with ubuntu, that can allow me to make cheap long distance calls to phones? I know Gizmo (which I don't like), and I don't know if there are any others...Any suggestions?

---

### Post by maniacmusician on 2006-11-06
I've heard that WengoPhone is good. Not sure. You can try it out.

---

### Post by nanotube on 2006-11-06
you could try the ekiga softphone (comes bundled with ubuntu).

---

### Post by PurplePenguin on 2007-03-17
I use Ekiga with voipdiscount.com (it's one of the BetaMax companies - there are about 10-20 of them, all the same company, but the rates are slightly different).  It works really well, and it's REALLY inexpensive.  

Here's the deal: you put 10 euros into your account.  This balance never expires.  You get 120 free days, so you can call any of the listed "free" countries for free (as long as you don't talk for more than 300 minutes, which is a lot, in a week) for 120 days.  After that, you've got to pay, but it's very inexpensive.  I make long distance calls to other parts of Canada, to the US and to Russia.  They're all free, after my 120 days are over, I have to pay 1.5 cents per minute to talk.  That's 1.5 cents a minute to call Russia!!  Unbelievable.  The voice quality is comparable to Skype, too.  

I've been using the service for a couple months, calling every day, and I've only spent about 1.5 euros (on calls to cellphones in Russia, which cost about 3.5 cents a minute if I remember correctly).  

The Ekiga softphone can be used with any of the other sip voip services out there that let you use your own softphone, too.

---

### Post by loell on 2007-03-17
i use gizmo, cause i can call freely to a home phone in the UK 

you can also use ekiga with gizmo account

---

### Post by edemark on 2007-03-17
Hi all

these days i am using wengophone (2.1 release is coming soon) but basically to have video conference with my mom also they have call out option though the 2.0 version has some problems with sound so you might wait till 2.1 comes out. Also you can try t out as the give you 25 euro cents of credit in the beginning.

On the other hand I would like to ask PurplePenguin about how he did set up ekiga with voipdiscount to be able to try that one out as these companies have some really low rates. So PurplePenguin please share your way of setting up ekiga.

thanks

---

### Post by bwallum on 2007-03-18
Anybody know of linux Skype version?

Rgds
Bob

---

### Post by PurplePenguin on 2007-03-18
> **edemark said:**
> 
On the other hand I would like to ask PurplePenguin about how he did set up ekiga with voipdiscount to be able to try that one out as these companies have some really low rates. So PurplePenguin please share your way of setting up ekiga.

Check out each of the Betamax sites to find the best match for the country you want to call ([here's a chart]("http://backsla.sh/betamax") showing cost comparisons), although they're the same company, the rates differ.

I found it quite easy to get voipdiscount.com working with Ekiga.  They've got an entry in their FAQ giving instructions to set up their service with any sip phone.  The biggest problems involved are 1. you need to use a Windows machine once (maybe it'll work with wine or virtualization) because your account gets created through the softphone you download from the site - once you set up the account, you can use Ekiga or any other softphone, and 2. each softphone uses different terminology, so you might have to play around to get the settings right.

Here are my voipdiscount.com settings from Ekiga:

Account Name: VOIPDiscount (this can be whatever you'd like)
Registrar: sip.voipdiscount.com
User: (your voipdiscount.com user name)
Password: (your voipdiscount.com password)
Authentication login: (your voipdiscount.com user name)
Realm/Domain: sip.voipdiscount.com
Registration Timeout: 3600

By the way, you don't have to pay anything to try it out.  You can make some calls for free, but I think they limit you to five minutes or so.  If it does work for you, I encourage you to support this really inexpensive voip service!!  It's so much cheaper than Skype!

Here's something that confused me for a while, until I googled it:

To make a call, just enter the phone number with two extra zeroes before it... eg. to call a USA number, enter sip:0015551234567@sip.voipdiscount.com with 555 being the area code and 1234567 being the phone number.  To call Russia, you'd put this in the calling field: [email]0075551234567@sip.voipdiscount.com[/email].  Just add two zeroes, then the country code (look this up on the net if you're not sure), the area code and phone number, @sip.voipdiscount.com at the end.

If you don't like Ekiga, this will work with any other softphone, but you'll need to figure out their terminology (eg. realm/domain and so on are often called other things).

**EDIT: ** Forgot to mention something about the setup... you can use the STUN setting in order to get around your NAT router if you've got one, but I found that it negatively affected sound quality.  So I went into my router and opened up the proper ports (1720, 30000-30010) and selected IP Translation instead of STUN in the NAT Traversal setting.  Now I get fantastic quality when calling land lines (although quality isn't great when calling Russian cellphones, but it's good enough considering it's only 3 cents a minute!).

---

### Post by PurplePenguin on 2007-03-18
> **bwallum said:**
> Anybody know of linux Skype version?

Rgds
Bob

I've used it, but as you can see from my other post, I tossed it in favour of Ekiga with voipdiscount.com.  It's a lot cheaper.

---

### Post by bwallum on 2007-03-19
Can you get Ekiga for Windows OS? The reason I ask is because lots of people I contact are on Windows and currently using Skype. I would like to point them towards Ekiga but that will only work if they can use a Windows app for it (yes I will get them on to Ubuntu soon but they need convincing - I get them to run applications in Windows then changing the OS is much less of an issue)

Regards
Bob

---

### Post by loell on 2007-03-19
> **bwallum said:**
> Can you get Ekiga for Windows OS? The reason I ask is because lots of people I contact are on Windows and currently using Skype. I would like to point them towards Ekiga but that will only work if they can use a Windows app for it (yes I will get them on to Ubuntu soon but they need convincing - I get them to run applications in Windows then changing the OS is much less of an issue)

Regards
Bob

ekiga for windows is not ready for primetime, since they use skype just use skype for linux to contact them. they might like to switch to ubuntu if they know that they can still use skype in linux.

---

### Post by PurplePenguin on 2007-03-19
> **bwallum said:**
> Can you get Ekiga for Windows OS? The reason I ask is because lots of people I contact are on Windows and currently using Skype. I would like to point them towards Ekiga but that will only work if they can use a Windows app for it (yes I will get them on to Ubuntu soon but they need convincing - I get them to run applications in Windows then changing the OS is much less of an issue)
Regards
Bob

I'm not a Windows user, so take what I'm about to write with a grain of salt. :)

If you want to chat Skype -> Skype, you can use it on Windows or Linux and chat with anybody using that protocol on either OS.

Ekiga is just one of the many softphones that you can use with a service like voipdiscount.com in order to make long distance calls, or ekiga.net to make softphone to softphone calls.  Anybody using any softphone (for any operating system) should be able to go to ekiga.net and apply for an ekiga account - you should be able to use this with any sip softphone to contact others, so Ekiga wouldn't be necessary to download for Windows users.

If your friends want to chat with each other and they're already happy with Skype, they might as well stick with it.  If they want to save some money on long distance calls, they can use the Windows client from voipdiscount.com (or one of the other betamax sites) and use it to call landlines.

EDIT:  I was trying to find the name of a new Windows/Linux voice/im client that I was looking at a few days ago, but didn't find it... I did find a really good [chart comparing VOIP clients]("http://en.wikipedia.org/wiki/Comparison_of_VoIP_software"), though!

---

### Post by cvmostert on 2007-04-28
> **PurplePenguin said:**
> I use Ekiga with voipdiscount.com (it's one of the BetaMax companies - there are about 10-20 of them, all the same company, but the rates are slightly different).  It works really well, and it's REALLY inexpensive.  

Here's the deal: you put 10 euros into your account.  This balance never expires.  You get 120 free days, so you can call any of the listed "free" countries for free (as long as you don't talk for more than 300 minutes, which is a lot, in a week) for 120 days.  After that, you've got to pay, but it's very inexpensive.  I make long distance calls to other parts of Canada, to the US and to Russia.  They're all free, after my 120 days are over, I have to pay 1.5 cents per minute to talk.  That's 1.5 cents a minute to call Russia!!  Unbelievable.  The voice quality is comparable to Skype, too.  

I've been using the service for a couple months, calling every day, and I've only spent about 1.5 euros (on calls to cellphones in Russia, which cost about 3.5 cents a minute if I remember correctly).  

The Ekiga softphone can be used with any of the other sip voip services out there that let you use your own softphone, too.

I also use ekiga with voipbuster.com  but i dont get good quality calls.. i dont know how i can get the quality better.. it gives me lots of problems... i so whish i could sort it out.. i also use wangophone.. and when the sound works.. it is great.. and skype of course.. has good soud as well.. it even works when i use other sound devices ... ekiga and wengo want to use the sound alone...

---

### Post by fragos on 2007-04-28
Check out [http://en.wikipedia.org/wiki/Ekiga](http://en.wikipedia.org/wiki/Ekiga) it mentions an Eikga for Windows beta.

---

### Post by danielph on 2007-05-23
On Linux I have found that twinkle outperforms ekiga with usability and voice quality. I consistently got better calls and found the interface friendlier. It was more informative as to what was happening and used a separate button to disconnect "bye". There is also a later version which does not have all the kde dependencies for those of you not using KDE If you are using KDE then it links up with kaddressbook apparently. If you just want a good SIP softphone, this is a good choice.

I have recently installed wengophone (2.1) and I am impressed how far this has come in the last year. I haven't thoroughly tested it, but the little I have used it has left me with a good impression. It also uses the gaim libs which give you access to your google chat, msn, icq, msn and any jabber clients.

On the windows side things are not so easy. As already said most people use skype and nothing is going to talk with this in the near future except another skype. I wont recommend the use of skype as I have doubts about its code and how it runs and information it may gather. That leaves Gizmo, Wengo and PhoneGaim. Wengo gets my vote here too, it is completely open source and seems to be moving in the right direction.

---

### Post by olavjunior on 2007-05-24
I've had big problems with getting sips to work at home. I've tried Gizmo, many times, but not being able to call other computers, only landlines. I tried Ekiga 2.0.3, called it from my n95, but the sound was horrible! Plain horrible!! Thought it had something to do with my router (and it propably does) 

Read the wiki that Ekiga 2.0.9 was released, so I thought, why not... Installed, and suddently the sound was, compared to earlier, GREAT!! 

( I got some error in the configure guide. It was in Norwegian, so something about the h323 and nat-type that I didn't understand)

EDIT: I'm hoping that someone can explain this to me: "Ekiga found symmetric NAT. If your router doesn't support H.323, you should foreward your traffic over the required ports to a locale machine, to change  symmetric NAT to conical"

How do I do this??

---

### Post by pgilmon on 2007-06-10
Check out [this thread]("http://ubuntuforums.org/showthread.php?p=2816025").

---

### Post by zedfrugnug on 2007-06-14
Has anyone used any of these programs succesfully with a usb-phone?
And is anyone using this to receive calls from people with regular phones?

I think I'll try justvoip.com, they're cheapest for calling to mobile in my country, and it should be possible to receive calls from regular phones.

Not sure which program I'll try first though.

---

### Post by jdackle on 2007-07-25
Great thread!!! :D

Ok, so here's my situation:
- I'm calling from Portugal (which probably doesn't matter as it's VoIP, right? **I'm a total newbie to VoIP**...)
- Calling **to a Portuguese mobile** that is currently located... erm.. in a boat somewhere in the Mediterranean...
- The above means the destination number is getting calls through **Roaming** service
- I want to make a call to this destination no. at **NO COST for the receiving mobile** and as cheap as possible for me, of course! :)

Questions:
- For what I've read, I'm leaning towards **ekiga. Any better sollution?**
- Are the prices in the charts given by two of the former posters in this thread **on the caller only or rather shared fees?** How do I find out about this?

Thanks in advance! :)

---

### Post by nanotube on 2007-07-25
> **jdackle said:**
> Great thread!!! :D

Ok, so here's my situation:
- I'm calling from Portugal (which probably doesn't matter as it's VoIP, right? **I'm a total newbie to VoIP**...)
- Calling **to a Portuguese mobile** that is currently located... erm.. in a boat somewhere in the Mediterranean...
- The above means the destination number is getting calls through **Roaming** service
- I want to make a call to this destination no. at **NO COST for the receiving mobile** and as cheap as possible for me, of course! :)

Questions:
- For what I've read, I'm leaning towards **ekiga. Any better sollution?**
- Are the prices in the charts given by two of the former posters in this thread **on the caller only or rather shared fees?** How do I find out about this?

Thanks in advance! :)

well, there is absolutely no way you can affect the fees that the receiving mobile is charged. when you use voip, you affect /your/ fees only, and all the prices given in charts are also your fees only. so, the receiving guy's fees only depend on the type of contract he has with his mobile provider, not on anything that you may do on your end.

---

### Post by jdackle on 2007-07-25
> **nanotube said:**
> well, there is absolutely no way you can affect the fees that the receiving mobile is charged. when you use voip, you affect /your/ fees only, and all the prices given in charts are also your fees only. so, the receiving guy's fees only depend on the type of contract he has with his mobile provider, not on anything that you may do on your end.

Yep... me and my friend confirmed that a couple hours ago (man, have you answered fast! :) ). As being abroad she's available only through roaming, she'll always have to pay for that service to her provider in Portugal...
Oh well...

Still, it's becoming a good learning experience for me. For starters, it'd be cheaper for us to talk on our mobiles through VoIP even if we were both in Portugal! :D

Cheers!

---

### Post by donkyhotay on 2007-07-25
I used to use skype but have begun moving to wengophone. The main thing I like about wengophone is that although it directs you to the wengophone service you can use it with other SIP services. It also is compatible with many IM protocols and has even replaced GAIM for me.

---

### Post by YannickDefais on 2007-07-25
Hi,

About Ekiga:
read the documentation: [https://help.ubuntu.com/community/Ekiga](https://help.ubuntu.com/community/Ekiga)

If you experiment bad audio quality, please upgrade to version 2.0.9 (see the doc) as even Ubuntu 7.04 Feisty ships Ekiga version 2.0.3 which is more than 1 year old now.

Regards,
Yannick

---

### Post by lisati on 2007-07-25
> **bwallum said:**
> Anybody know of linux Skype version?

Rgds
Bob
I have skype up and running now on my laptop which only has Ubuntu - visit [www.skype.com](www.skype.com) and click on the "download" option in the menu (but NOT the green download button) - you should be given a choice.


p.s. Skype can accept payments through PayPal

---

### Post by olavjunior on 2007-10-03
> **PurplePenguin said:**
> 

Here are my voipdiscount.com settings from Ekiga:

Account Name: VOIPDiscount (this can be whatever you'd like)
Registrar: sip.voipdiscount.com
User: (your voipdiscount.com user name)
Password: (your voipdiscount.com password)
Authentication login: (your voipdiscount.com user name)
Realm/Domain: sip.voipdiscount.com
Registration Timeout: 3600


Hy! I'm having some issues with ekiga. I always get registration failed..

Registrar: sip.voipdiscount.com
User: myusername (not: sip:myusernam@sip.voipdiscount.com?)
password: mypassword
more alternative:
logg in for authentication: sip.voipdiscount.com
 timout: 3600

(I've translated from Norwegian, so I'm not sure of the field names in english)

Then I've also set the port to 5060 in preferences for H.323. Other then that, I've left it as is. (no outgoing proxy, no nat-handeling)

So it's my registration that failes. Have you got any ideas?

EDIT: Solved it. Instead of sip.voipdisount.com at the "logg in for authentication", I had to use my username, naturally. I guess they've changed ekiga since your tutorial. Now everything workes fine! :) I'm very happy

---

### Post by gatewayasteroid on 2007-10-03
> **rozojc said:**
> Besides skype, what is the best program, also available under linux and compatible with ubuntu, that can allow me to make cheap long distance calls to phones? I know Gizmo (which I don't like), and I don't know if there are any others...Any suggestions?

I was very disappointed with some Ekiga bugs...so I'm using Twinkle since last year, I found it very good.

---

### Post by Loan_Refi on 2007-12-19
Eyebeam works well on Ubuntu!!

FYI to all I'm running eyebeam 1.5.17 under wine in Ubuntu 7.10. Calls in & out work excellent as well as call transfer & hold button. 
Sound quality is crystal clear

My system info;
Dell Inspiron 300m 1.2 GHz Pentium M 1g Memory 60g Hardrive

I have installed Ubuntu 7.10 & Vista Enterprise on same machine dual boot. Vista and Eyebeam do not work well together with my dell 300m but it does work well with Ubuntu.

Give it a try you'll like it!!

---

### Post by rykel on 2008-05-18
Hi,

I have a BIG problem with Ekiga... it fails to login to my voipdiscount SIP account, AND my ekiga account. (irony!)

Oh, and in the last 2 days, Ekiga has been telling me that its port is used by something else, but there is no other SIP phones running... and I know Skype is not using it either.

See the screenshots for the errors.

Still on the topic of Ekiga, how do I know if it is trying to auto-reconnect to the SIP server, IF it is? If not, how do I set it to auto-reconnect?

Thanks for helping!!

p/s. These errors did NOT exist before, and I was able to register to the SIP services OK and make/receive calls.

---

### Post by neerajadsul on 2008-05-21
For me, I use TWINKLE, it worked really well without any problem.
I use VOIPBUSTER and VOIPWISE services.

---

### Post by rykel on 2008-05-21
Hi,

Does anyone else here use Voipdiscount?

Although it is supposed to be FREE unlimited calls to landlines, I found out that there is a "connection charge" of 5 euro cents. This makes the service impractical for short calls ("OK, meet me at 3pm."-type)...

Do you know which other SIP provider provides FREE unlimited calls to more than 30 countries AND does not have a connection/hidden fees AND can be used in Ekiga, Twinkle, Wengo, Fring, Talkonaut etc.?

Thanks for advising!

---

### Post by gorski on 2008-06-03
Thank you, PP! Very useful! Done it!:guitar:

Mind, I can't place videocalls to 3G - anyone managed to do it, please and how, if so?:confused:

---

### Post by rykel on 2008-06-04
Hi friends,

I have been experimenting with OpenWengo 2.1.2 (from Hardy repository), Ekiga, Twinkle, Gizmo5, Jabbin and Empathy. On my Nokia 6121 Classic I have tried Fring, Talkonaut, Gizmo5, Nimbuzz and Symmy.

Right now, I have settled down on running both Meebo.com, OpenWengo and Skype side-by-side with each other, with Fring and Gizmo5 on my mobile phone.

[INDENT]**Meebo.com** - for all my IM. I prefer my chat logs to be stored in the clouds.
**OpenWengo** - Works well with VoipDiscount. Just log out and create a new Profile to log in with the VoipDiscount info.
**Skype** - For IM with Skype users, what else. If only Meebo.com or OpenWengo support Skype and voice or vice versa...   : (
Fring - Closed source but the best all-in-one. It connects to all my IM, including Skype AND can make both SkypeOut and SIP calls. 2 caveats though: Fring does not have SMS and you can only see the nicknames not email addresses of your IM buddies.
Gizmo5 - I leave this on my phone purely for SMS purposes.
[/INDENT]

Why not Ekiga, Twinkle, Gizmo5, Jabbin or Empathy?

**Jabbin and Empathy** are both not mature enough yet, imho. The interface, ease of installation, ease of setting up, number of users adopting them etc. all beg for more time.

Twinkle is a KDE program but I prefer non-KDE programs if available, because KDE software usually shows every single option available in any configuration dialog instead of offering Basic and Advanced views. That is, too time-consuming trying to read or figure out what each option means!! *ready for KDE flames*   :guitar:

Gizmo5? Proprietary software that is almost perfect, but does NOT allow you to use their competitors' SIP services. (eg. VoipDiscount) It does pretend to connect for a while, though. p/s. Gizmo5 SMS on Symbian S60 phones is good! Fring, Talkonaut and possibly Nimbuzz do NOT have SMS.

Ekiga? The WORST of the lot. Cannot register to VoipDiscount service, and worse, cannot register to its own Ekiga.net service even!

On the phone, Talknonaut, Nimbuzz and Symmy are out. Talkonaut only works well with SipPhone or their own service providers and refuses to work consistently with VoipDiscount. Nimbuzz seems to use PSTN for some stuff (cannot recall offhand) so it defeats my vision of communicating on 3G Internet-Only. (To be fair to Symmy, I did not get to use it yet, since I was too lazy to create yet another VoIP account)

Having said everything, I hope that Fring can become Open Source AND continue to innovate, lead and improve. (eg. allowing users to see their buddies' email addresses)

Last but not least, I hope that OpenWengo gets into version 2.2 soon, as I read that the future of the project is currently uncertain due to it no longer having any corporate leadership. If you are a developer who loves open source VoIP, I implore you to help OpenWengo!

Hope that helps.

---

### Post by LindaLou on 2008-07-11
Hello All,  I'm new to the forum.  Today I installed Ubuntu and am quite pleased.  Hope that you all will be able to forgive this newbie for any lame mistakes!  I was using voipdiscount.com for a few years with my MS operating system and read in these threads that others are using the same voip system with Ubuntu.  My question is: Do I have to interface voipdiscount.com with Ekiga Softphone and if so how is this done?  
Please be kind as I am sooo new to Linux, still wet behind the ears!  
I appreciate all your assistance, advice.

Regards, LindaLou

HP Pavilion zv5000, 512 MB, AMD64 Athlon, DVD/CDRW, NVida

---

### Post by danielph on 2008-07-12
> **LindaLou said:**
> Hello All,  I'm new to the forum.  Today I installed Ubuntu and am quite pleased.  Hope that you all will be able to forgive this newbie for any lame mistakes!  I was using voipdiscount.com for a few years with my MS operating system and read in these threads that others are using the same voip system with Ubuntu.  My question is: Do I have to interface voipdiscount.com with Ekiga Softphone and if so how is this done?  
Please be kind as I am sooo new to Linux, still wet behind the ears!  
I appreciate all your assistance, advice.

Regards, LindaLou

HP Pavilion zv5000, 512 MB, AMD64 Athlon, DVD/CDRW, NVida
Hi LindaLou,

and welcome.

Yes you need to setup Ekiga to use your voipbuster account. It is a good idea to go through the startup wizard in Ekiga also. New accounts can be created by going to accounts setup in ekiga (**Edit -> Accounts -> Add)** and adding a new account.The server is voipbuster.com and then you just need your user name and password. Click the checkbox and make it your default account and voila. The other options you can leave as default although you may want to use a stun server if you are behind a NAT router (as most home routers are), you can use stunserver.org or the defaults if there is one.

If you get stuck let me know and I'll give you step by step instructions. There is also some more information [here]("https://help.ubuntu.com/community/Ekiga")

Hint: normally you can raise a new issue for new problems by creating a new thread in the relevant forum

---

### Post by LindaLou on 2008-07-15
Thanks danielph,  I appreciate your help. I read thru the link you provided as I am now experiencing "Registration failure: forbidden" error showing up at the bottom of Ekiga when I open it up this morning. I have double checked that the registration info (name, password) are identical with both ekiga.net as entered with the Config Asst.  I did add voipdiscount as per your instructions but when I open Edit>Accounts both ekiga and voipdiscount.com show "Registration Failed". I have STUN set.  I feel like a fish out of water.  Usually I can figure this type of thing out but being a freshly brewed cup of Ubuntu is quite frustrating and a bit red in the face!  ](*,):oops:
I have gone thru the ekiga q&a at launchpad.net - searching everywhere!  I KNOW this ekiga will work!!  and I am appreciative of you assistance.
Until later.  
p.s. I have noted your "hint" and will make sure of this in the future. Thanks

---

### Post by danielph on 2008-07-16
Being a freshly brewed cup of coffee doesn't sound so bad :) Better than being instant!

Can you try running the configuration assistant and tell me what is reported for the NAT test?

---

### Post by LindaLou on 2008-07-16
[FONT="Arial"]Here's the result from the NAT Detection:[/FONT]
[FONT="Comic Sans MS"]Ekiga detected Symmetric NAT.  The most appropriate method, if your router does not natively support SIP or H.323, is to forward the required port to your internal machine in order to change your Symmetric NAT into Cone NAT.  If you run this test again after the port forwarding has been done, it should report Cone NAT.  This should allow Ekiga to be used with STUN support enabled.  If it does not report Cone NAT, then it means that there is a problem in your forwarding rules.
[FONT="Arial"]I was reading about this earlier today at this site [http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router#Getting_it_to_work_behind_a_NAT_router](http://wiki.ekiga.org/index.php/Ekiga_behind_a_NAT_router#Getting_it_to_work_behind_a_NAT_router).   The thing is I'm not sure how I am able to access the D-link router.  I've only had a few issues with my internet service provider where I had to access the D-link and for the life of me I cant remember.  You might think that a simple phone call would suffice, but believe me, where I'm at simple is the last word for anything!!  If need be I can figure it out or phone.  
Oh, and good come back with the "better than being instant".  LOL!!  [/FONT][/FONT]

---

### Post by danielph on 2008-07-17
It asks to run the test again and it should report Cone NAT. If it does not then there maybe a forwarding problem. Most routers can be accessed through a web interface. Simply typing in the IP address of your router (Normally it is 192.168.0.1 or 192.168.1.1)  into the web browser (eg firefox or whatever you use)  would get you there. 

Depends on what model it is if it supports web interface. I had a dlink and it had a web interface. If yours doesn't then you sometimes get install disks for windows to access and configure the router.

---

### Post by rykel on 2008-07-19
Hi guys (LindaLou = female?),

As I mentioned in my post above, Ekiga is the WORST software for connecting with Voipdiscount as LindaLou has personally witnessed.

Fortunately, in Linux, we have choices, and in this case, LindaLou, I would suggest that you download OpenWengo, a program that looks like Skype, but connects to Voipdiscount AND the major Instant Messaging networks.
[B][INDENT][LIST=1]
[*]System
[*]Administration
[*]Synaptic Package Manager
[*]Search
[*]"wengo"
[*]Select and Install
[/LIST][/INDENT][/B]

You should make sure that your OpenWengo is at least at version 2.1 or 2.2.

It is very similar to your MS client from this point on.

Let me know if you need further help.

btw, Voipdiscount seems to have INCREASED their SMS to 3 cents per message, instead of the usual 1 cent, and deducts 5 cents even for unconnected calls.

---

### Post by LindaLou on 2008-07-19
Yup LindaLou does = Female!!  Family nickname and it just kinda stuck.
Thanks for the OpenWengo info. Other than the 6 steps you listed, are there any others such as configuration like you do in Ekiga??  or any definite configurations that I should know about?  Appreciate your info and input Rykel.

---

### Post by LindaLou on 2008-07-19
Hi Danielph, I did get into the router setup and it is set to NAT.  Not sure about the Cone NAT but definitely have it set up for NAT.   Is this correct?  or should I be looking at something else?

---

### Post by LindaLou on 2008-07-19
Followed your steops for Wego.  Went to install and the following pop up for changes to be applied and just wondering if this is all correct. It states that "15 new packages will be installed, 146 MB extra space will be used, 49.9 MB to be downloaded" and then there is a choice to "Download package files only" and of course "Cancel or Apply"  I am not 100% sure about this download - not sure if I should download package files only (what would be missing if I did this).  Feeling really Blonde with Ubuntu and am so grateful for you help.:
libaudio2 (version 1.9.1-1) will be installed
libavcodec1d (version 3:0.cvs20070307-5ubuntu7) will be installed
libavformat1d (version 3:0.cvs20070307-5ubuntu7) will be installed
libavutil1d (version 3:0.cvs20070307-5ubuntu7) will be installed
libboost-program-options1.34.1 (version 1.34.1-4ubuntu3) will be installed
libboost-regex1.34.1 (version 1.34.1-4ubuntu3) will be installed
libboost-serialization1.34.1 (version 1.34.1-4
libboost-serialization1.34.1 (version 1.34.1-4ubuntu3) will be installed
libboost-signals1.34.1 (version 1.34.1-4ubuntu3) will be installed
libboost-thread1.34.1 (version 1.34.1-4ubuntu3) will be installed
libdc1394-13 (version 1.1.0-5ubuntu1) will be installed
libgsm1 (version 1.0.12-1) will be installed
libqt4-core (version 4.3.4-0ubuntu3) will be installed
libqt4-gui (version 4.3.4-0ubuntu3) will be  installed
wengophone (version 2.1.2.dfsg0-3) will be installed
wengophone-dbg (version 2.1.2.dfsg0-3) will be installed

---

### Post by loell on 2008-07-19
hi, sorry to butt in with your conversation with your current conversation,
if i may..  Yes its that large, just install it (those are necessary files) and wengophone will be installed.

I don't want to confuse you but in my opinion, **twinkle** is most likely the counterpart of ekiga. anyway do try wengophone.

---

### Post by LindaLou on 2008-07-19
Hi loell, I'm open to all opinions, being a freshly brewed cup of Ubuntu all programs are new and I'm willing to investigate all until I find the one that will allow me to use my voipdiscount.com.  As I mentioned previously, I used voipdiscount.com to phone out from Brasil, and it is very necessary for my work.  I'll google twinkle and in the mean time would be able to give me any pointers or more info?

---

### Post by loell on 2008-07-19
yeah, here is there homepage.

[http://www.twinklephone.com/]("http://www.twinklephone.com/")

to install this in ubuntu, just check **twinkle** in **add/remove programs**


or better yet if you're in ubuntu hardy heron, just [click this to install Twinkle]("apt:twinkle") :)

---

### Post by LindaLou on 2008-07-19
So, no special configuration needed??  Just a simple download then?:-k

---

### Post by loell on 2008-07-19
well, you have to input your account to use it, but apart from that, no other configuration is needed.

---

### Post by LindaLou on 2008-07-19
I was just looking at the screen shots on the twinkle web page and am wondering if any of the following (used for Ekiga set up for voipdisocunt.com) is going to necessary:

 Adding SIP account
Account name: VoipCheap (free to choose)
Protocol: SIP
Registrar: sip.voipcheap.com
Username: (username from voipcheap)
Password: (password from voipcheap)
Authentication Login: (username from voipcheap)
Realm/Domain: voipcheap.com
Registration Timeout: 3600

And then close accounts window.

5. Preference settings
-Go to Edit/Preferences
-Go to General/SoundEvents and set alternative output device to default.
-Go to Protocols/NetworkSettings
NAT Traversal Method: STUN
Stun Server: stun.voipcheap.com
and then click on Apply.
-Go to Protocols/SIPSettings
Outbound Proxy: sip.voipcheap.com
-Go to Devices/AudioDevices
Audio Devices Output Device: default
Audio Devices Input Device: default

---

### Post by loell on 2008-07-20
yeah, the usual setting, except for the outbound proxy, voipdiscount don't seem to have one.

---

### Post by LindaLou on 2008-07-20
thanks.  If I come up against any problems I'll be sure to post and ask for some help.
Can you tell me if the connections from pc to land lines is good, decent, excellent?

---

### Post by loell on 2008-07-20
i think it varies from codecs being used.

---

### Post by rykel on 2008-07-20
Hi LindaLou,

Yes, you need to set up OpenWengo to use Voipdiscount.

I have attached a series of screenshots in pdf format so that you can visualise how it is done.

[INDENT][B][LIST=1]
[*]Login Screen
[*]Other (For Power Users Only)
[*]Account: Anything you fancy
[*]Login: Your Voipdiscount Username
[*]Password: Your Voipdiscount Password
[*]Domain: sip.voipdiscount.com
[*]Displayname: Anything you fancy
[/LIST][/B][/INDENT]

I have tried it many times, and it should work for you too.

---

### Post by danielph on 2008-07-20
Glad to see the thread founds its way back on topic :mad:

I think @LindaLou you may find yourself doing the same as many others and trying a few and seeing what fits. I personally use twinkle as I find it simple and reliable and I run KDE rather than gnome. This is not a biggy as it can be used with gnome without a problem. I also have ekiga working, but as mentioned and as you can see it is a pain.

Wengo I never found worked that well for me, but may have improved by now. 
Gizmo is another one you can look at. 

good luck with whatever you decide.

---

### Post by LindaLou on 2008-07-20
Thanks Danielph, for you input.  And thank you to all that have done the same. ;) Today is the day that I put all this info to the test!!  Once I'm up and running, I'll be sure to post that let all know my success.  If I should run into any "problems" (dont like that word), I'll be posting like crazy!!  looking for answers !! [-o<

---

### Post by LindaLou on 2008-07-20
I was really hoping to post a positive about Twinkle, but I just havent been able to work out the issues I'm having:
1.  Installed Twinkle 1.1 via Add/Remove Programs.
2.  Entered data as necessary for voipdiscount.com
3.  Entered phone number and received this message:

"Sun 23:57:03
Critical: Cannot open ALSA driver for PCM playback: Device or resource busy"

4.  Also, received error message that the speakers and mic were not found.  I switched the settings around - ALSA Default, OSS Default, etc. Thought I got a call thru as Twinkle responded with "Line 1: far end answered call."  I didn't hear a thing thru my headset.

5.  Tried another number and this was the response "Line 1: call failed.
404 Not Found"

6.  Tried a third number and was back to getting error messages about the speakers and mic.

When I went back to System Settings>Audio to make changes to the speakers and mic the settings were not as I had left them, and were now all at ALSA Default.  It is noted on this tab that it is not recommended to use ALSA Default for the mic if this default is used for the other settings.  I have changed it but it just doesn't want to stay.  

What are the remedies to this situation?  I'm also looking up the answer(s) on the twinkle forum, but I have yet to receive any fed back.  Hope you all will be able to guide me in the ight direction!

Thanks for your help.

---

### Post by loell on 2008-07-21
sadly, you're on the era of linux sound system transition phase :(

but i found this [blog post]("http://ultrahigh.org/2008/05/")

which basically says the work around, and i qoute the fix

> Set it to use OSS for audio input and output, set the ringing to use ALSA default device (which is pulseaudio) and start the program with &#8216;padsp twinkle&#8217;

hope it helps..

---

### Post by LindaLou on 2008-07-21
Hi loell, Murphy's Law I guess!! re - Linux transition !  

Thanks for the link/blog info. here is what the Profile looks like. Wondering if this is ok or if some of the available codecs need to be added.  Also, I'm not familiar on how to and start the program with ‘padsp twinkle’ .  Please, would you mind explaining this.  

On a separate note, I would just like to say, that you all have great patience for us "newbies"!!  I am soooo looking forward to being a gourmet cup of Ubuntu rather than fresh brewed!!  Not holding my breath on that one :roll: - just getting into my second week here!!  

Thanks again.

---

### Post by loell on 2008-07-21
don't worry about the codecs, mostly they are standards,

to execute **padsp twinkle** just type it in the terminal, there should be a terminal icon on your desktop.  if this command will now give you sound in twinkle then we could just make a shortcut icon or a luancher for this command.

---

### Post by LindaLou on 2008-07-21
Here's a screen shot of the results.  What am I doing wrong?  When I went to open twinkle I received the following errors:

Cannot resolve STUN Server" stunstun01.voipdiscount.com

Cannot access the ring tone device(ALSA:default)
Cannot access the speaker (ALSA:default)
Cannot access the microphone (ALSA:default)

After clicking "ok" to the 2 error pop ups, twinkle opens.  

I feel that I must have missed a step or something, or....  When typing in the padsp twinkle into the terminal, I did not have twinkle open yet, just fyi.

---

### Post by loell on 2008-07-21
according to [http://www.voipdiscount.com/en/sipp.html]("http://www.voipdiscount.com/en/sipp.html")

the stun server should be **stun.voipdiscount.com** not stunstun01.voipdiscount.com

before executing **pdasp twinle**, have you already configured twinkle previously and set it to OSS for audio input/output, and the ringing to use ALSA default device?

---

### Post by LindaLou on 2008-07-21
I have gone into the settings a set to OSS but it wont stay applied.  I have corrected the stun.voipdiscount.com error. Thanks for pointing that out to me.  Is there a way to to the initial "wizard" configuration again, or will I have to uninstall and reinstall twinkle to correct what ever mess I seem to have made here!!  :confused:

---

### Post by rykel on 2008-07-23
LindaLou, Twinkle - once set up properly - WILL work with Voipdiscount very well with great sound quality. I have used it with complete satisfaction too.

However, if you are a newbie, you might want to set up Wengo first because as you have discovered by now, anything KDE is very powerful, so powerful and precise to the point that you need to spend time getting configurations and placing them into the right fields... a couple of small mistakes and you cannot get a KDE program to work.

Let us know once you have success ~ and you WILL have success simply because so many of us have made Voipdiscount work on Ubuntu Linux.

---

### Post by LindaLou on 2008-07-23
Thanks Rykel,  I'm going to work ont twinkle today as I would really like it up and running.  I've read as many post/threads on both wengo and twinkle and from what I can gather, twinkle give the best sound, as you mentioned.

You're right about the KDE!  I've noticed changes - transparent windows when I expand a minimized window, clicking on the FF icon gives this nifty swirl effect, and a few others. and not sure if I'm all for it. Haven't had time to delve into KDE, unfortunately.

I was thinking that maybe I should just uninstall twinkle and start from scratch(?), since you mentioned how one small mistake can mess up the program. Any opinion on this?

Thanks again for your assistance.:)

---

