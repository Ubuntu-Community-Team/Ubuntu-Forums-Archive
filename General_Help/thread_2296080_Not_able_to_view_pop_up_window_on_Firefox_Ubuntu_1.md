---
title: "Not able to view pop up window on Firefox Ubuntu 14.04"
date: 2015-09-23
forum: General Help
---

### Post by suparna-diwakar on 2015-09-23
I am on Ubuntu 14.04, Firefox 38.0. I am not able to read popups that I want to read. Eg, on my bank website for netbanking. Attached screenshot of another site as an example. Will deeply appreciate some help!
Thanks in advance,
Suparna

---

### Post by vasa1 on 2015-09-23
What happens if you try the niti.gov.in site with all add-ons disabled? To do so, click Help, Restart with addons disabled ...

I don't see any pop-up with the site. There is a full-width "slide show".

I'm on Firefox 41, if that matters.

---

### Post by suparna-diwakar on 2015-09-23
Actually, I was trying to open the Data.gov website (icon at bottom of page) when I got that message. In netbanking this happens all the time. I get a screen like what I had shared in the screenshot. Is it possible that the font cannot be read?
I did try disabling addons, opened in safe mode etc. Did not work.

---

### Post by Bucky Ball on 2015-09-23
Do an update via Software Updater or try this:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

It won't upgrade your current OS to a newer one. Firefox 40.0 is the current one in the 14.04 repositories. You have java installed? Make sure you update first.

```
sudo apt-get install openjdk-7-jre
sudo apt-get install openjdk-7-jdk
```

Or install both from the Software Centre. :)

---

### Post by suparna-diwakar on 2015-09-23
Okay. Thanks. Will try that. Yes. I have Java installed. But I think there are two versions of it in Synaptic that I saw. Am afraid of doing anything with it because I don't want some dependencies going haywire!

---

### Post by Bucky Ball on 2015-09-23
```
sudo apt-get autoremove
```

See what that kills. If you don't install java manually and stick to the repositories don't worry about dependencies.

---

### Post by vasa1 on 2015-09-23
> **suparna-diwakar said:**
> Actually, I was trying to open the Data.gov website (icon at bottom of page) when I got that message. In netbanking this happens all the time. I get a screen like what I had shared in the screenshot. Is it possible that the font cannot be read?
I did try disabling addons, opened in safe mode etc. Did not work.
Try some other theme. For me, the "pop-up" (or dialog window) has this: "You are going to visit external link, Are you sure to continue?" The two buttons are "Cancel" and "Okay".

---

### Post by suparna-diwakar on 2015-09-23
[FONT=tahoma]I did the dist upgrade. Have firefox 41 now! But still no luck. Will try the java thing and get back. Vasa 1 this is happening to all such windows! Is it some font issue, you think?
Thanks for your help. Will come back with feedback...
[/FONT]

---

### Post by suparna-diwakar on 2015-09-23
[FONT=tahoma]I did the dist upgrade. Have firefox 41 now! But still no luck. Will try the java thing and get back. Vasa 1 this is happening to all such windows! Is it some font issue, you think?
Thanks for your help. Will come back with feedback...
[/FONT]

---

### Post by suparna-diwakar on 2015-09-23
I [FONT=tahoma]I am back! Had the jre not jdk. So installed. Still not able to see the what the popup is saying![/FONT]

---

### Post by suparna-diwakar on 2015-09-23
No[FONT=tahoma]Now I have a new problem. After the upgrade, Google Home Page is not showing all the fonts. Can I downgrade to Firefox 40 from Firefox 41?[/FONT]

---

### Post by suparna-diwakar on 2015-09-24
I managed to sort out the issue ...with the help of friends at ITfC, Bangalore. This is what I did:
1. Disabled all the addons that "could not be verified by firefox".
2. Changed the font under Preferences>Content>Advanced to sans-serif as shown in the screenshot. 
But I still am not able to choose the "allow website to choose their own fonts....". I can live with that!
Thanks a ton to everybody on the forum. I am closing this post as solved. Hope it helps somebody...
Regards,
Suparna):P

---

