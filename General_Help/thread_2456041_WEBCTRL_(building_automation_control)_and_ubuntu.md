---
title: "WEBCTRL (building automation control) and ubuntu"
date: 2021-01-03
forum: General Help
---

### Post by sarwiz on 2021-01-03
Not sure where to post this. I am working on a computer for work, and would like to run webctrl 6.0 on Ubuntu. This will be for a backup system until we get our new automation HVAC computer. HDD on the old one went bad, but i had a backup of the system saved on a usb drive. It was running on windows 7 before, but constantly had stability and reliability issues. i am a novice ubuntu user, but have used it on a computer at home. Does anyone have experience with setting this up, and maybe a tip or trick or 2. Thank you

---

### Post by CelticWarrior on 2021-01-04
As the name "web" suggests, its requirements are a fairly up-to-date web browser, Chrome or Firefox.
Knowing this I really don't understand your question? Something intended to be manged via a web browser is almost always OS agnostic.

---

### Post by sarwiz on 2021-01-04
What we had was a main server running on a win 7 computer. It contains all the uploaded files and programs for the invividual controllers. The main prg ill be working withis Eikon Logic builder for modifying the controller parameters. but , now thinking about it, out system is totally in house with no connection to outside internet. It probably will run just fine on ffx or chrm, as long as they are v66.0 and v60.0 respectively, (got that from the webctrl website). Going to try it tomorrow. It will be a clean ubuntu 20.04 install on a blank HDD. Once installed, Ill port my phone in to connect for updates (EasyTether, best 10 dollars i ever spent, 11 years ago.) Ill post here again in the next few days.

---

### Post by CelticWarrior on 2021-01-04
> [COLOR=#000000](EasyTether, best 10 dollars i ever spent, 11 years ago.)[/COLOR]

If you say so... Well, if you're still using the same (non-smart) phone than yes, that was one of the most popular solutions back then. Nowadays any iPhone or even the cheapest Android have that functionality built-in.

---

### Post by sarwiz on 2021-01-04
If you say so... Well, if you're still using the same (non-smart) phone than yes, that was one of the most popular solutions back then. Nowadays any iPhone or even the cheapest Android have that functionality built-in.

And how much do they charge per month for it? When we had verison, they wanted 30 a month to use the tethering. i have an s10. Would never go anywhere near an apple product. It may be built in, but they charge you for it. the 10 was a ONE-TIME Fee.

---

### Post by CelticWarrior on 2021-01-04
> [COLOR=#000000]And how much do they charge per month for it?[/COLOR]

In the US maybe some extortionist service providers do charge for it. In Europe? No, nothing, nada... It doesn't matter how you spend your data plan, for the apps installed in your phone or for anything else connected to it regardless of the method or type of connection (USB, WiFi, Bluetooth). It is as it should be.

---

### Post by sarwiz on 2021-01-04
You got that right, I think they are all extortionists here.

---

### Post by wildmanne39 on 2021-01-04
@sarwiz, are you saying that cell phone providers in the U.S. charge to use the tethering feature? please let's  not call any company's extortionists on the forum.

---

### Post by sarwiz on 2021-01-05
Ok, installed 20.04, and cannot get anything to install. The webctrl disk actually had some linux install files, but just did not work. They are .sh file.
Also could not get my easytether to install, and its a .deb file, just did nothing

---

### Post by rsteinmetz70112 on 2021-01-05
I think we need some more information on your install and hardware. Were you able to update 20.04? I expect not since you can't get easyteather to install. 
Are you sure the ubuntu drivers you have are the correct ones for you computer and Ubuntu 20.04? They seem, to be available of the website. WEBCTL seems to be Java based so is java installed?
You say your have a WEBCTL Disck , what is is a DVD and can you read the files on it?
When you say the .sh files did not work, how did you try to start them and what happened?

---

### Post by sarwiz on 2021-01-06
Cannot connect to net, computer is a dell optiplex 64 bit that used win 7 when new. Ill have more details later on it. I might have to take it home, and reinstall while connected.

---

### Post by rsteinmetz70112 on 2021-01-06
There really is no easy way to install Ubuntu without an Internet Connection. It is possible to download all of the repositories elsewhere and connect an external drive to the machine but then updating is a real pain, although you don't need as much security if you aren't connected to the net.

Also are you sure you can't use tethering or a WIFI hotspot from your phone? I have ATT and my (business) plan  includes both. As far as I can tell only the basic plans don't. They have added it to some plans in response to COVID. Not sure about other carriers, but the plans change all the time.

---

### Post by sarwiz on 2021-01-07
Yeah, I should have just taken it home in the first place. project on hold for now, but will probably be digging back into it next week. Management here is not up to par on building controls, and its like they just dont think its important, until something goes wrong. The system is running automonously right now, since each controller has its own program, and a lot of things are in manual mode. I'll post more on this later. it is becoming a kind of hobby project to me now. ( I think I can, so I shall!!) I have been using Ubuntu since about 2006, but have not really dug in enough to really learn it. Time is now.

---

