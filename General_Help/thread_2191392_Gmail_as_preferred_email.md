---
title: "Gmail as preferred email"
date: 2013-12-02
forum: General Help
---

### Post by jdrc on 2013-12-02
Hi - I just loaded Lubuntu onto my netbook, and I'm pretty happy with it so far.  One issue is that I can't seem to find any information on switching to Gmail as the preferred email application.  I've found and tried Ubuntu-related fixes, but can't get them to work, so I'm guessing that there's a different way to do it in Lubuntu.

Thanks!

---

### Post by erasmusp on 2013-12-02
Does Thunderbird install in Lubuntu? Not sure what you mean with "Ubuntu-related fixes"...

---

### Post by jdrc on 2013-12-02
I meant that they seemed not to work for Lubuntu.  I still don't understand the hierarchy, so maybe I'm off base (does anything that works for generic Ubuntu work for Lubuntu?).

---

### Post by jdeca57 on 2013-12-02
> **jdrc said:**
> Hi - I just loaded Lubuntu onto my netbook, and I'm pretty happy with it so far.  One issue is that I can't seem to find any information on switching to Gmail as the preferred email application.  I've found and tried Ubuntu-related fixes, but can't get them to work, so I'm guessing that there's a different way to do it in Lubuntu.

Thanks!
If Sylpheed is still the default e-mail client in Lubuntu the following can be found in it's FAQ:
> 
2.4. 	How do I set up an account?
	
After loading Sylpheed for the first time, you can add an email account by clicking the Configuration menu. Select the option Create new account and let the configuration assistant help you with the initial setup. In a few easy steps, the assistant allows you to conveniently configure your POP3, IMAP4, or Gmail account. 

But of course Thunderbird also works with Gmail, I use it that way. (but not with Lubuntu)

---

### Post by jdrc on 2013-12-02
Sorry, I guess should have been more clear: I want to make Gmail open with a new message when I click a "mailto:" link on a website (or from elsewhere, I suppose).

Thanks!

---

### Post by ajgreeny on 2013-12-02
> **jdrc said:**
> Sorry, I guess should have been more clear: I want to make Gmail open with a new message when I click a "mailto:" link on a website (or from elsewhere, I suppose).

Thanks!

Gmail is not an application that you can open.

You must either use a mail client such as thunderbird or sylpheed, or use the webmail in your web-browser, though I am not sure how you manage to get to a webmail page from a **mailto** link.

What happens at the moment when you click on mailto links; does sylpheed open?

---

### Post by jCjQszKMO5JH on 2013-12-02
In Windows, your web browser can register Gmail as an application to handle mailto links. I don't think that's the case in Ubuntu. This link has a workaround though:

[https://wiki.ubuntu.com/Gmail](https://wiki.ubuntu.com/Gmail)

I'm not sure how to handle preferred applications in Lubuntu though, as it's been a while since I've used LXDE.

---

### Post by jdrc on 2013-12-02
I've been using Chromium, and when I click an email address from a website, Sylpheed opens.  I installed Gnome Gmail and made it my preferred email app, but nothing happens in Chrome.

I tried Firefox, and the Gnome Gmail function worked: when I clicked the contact email in a Craigslist ad, a new tab opened with Gmail's compose message setup.

So, any way to get this to work for Chrome?

---

### Post by jdrc on 2013-12-02
> **mascafidi said:**
> In Windows, your web browser can register Gmail as an application to handle mailto links. I don't think that's the case in Ubuntu. This link has a workaround though:

[https://wiki.ubuntu.com/Gmail](https://wiki.ubuntu.com/Gmail)

I'm not sure how to handle preferred applications in Lubuntu though, as it's been a while since I've used LXDE.

Yikes.  I tried the first suggestion in that page, and it's not working.  Am I supposed to paste that entire line [FONT=courier new]([/FONT][COLOR=#333333][FONT=courier new]bash -c 'sensible-browser "https://mail.google.com/mail?view=cm&tf=0&to=`echo %s | sed 's/mailto://'`"'[/FONT]) into the Custom Command Line?  When I do, it just reverts back to Sylpheed.

I started to try the second suggestion, but that's over my head.  I pasted the script into a text file, saved it as a .sh, and then got lost.[/COLOR]

---

