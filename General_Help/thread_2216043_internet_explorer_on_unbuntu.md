---
title: "internet explorer on unbuntu"
date: 2014-04-09
forum: General Help
---

### Post by robbiejormerod on 2014-04-09
I know this sounds stupid, but is it possible to get internet explorer on Ubuntu. Not that I like IE or anything but British Gas for some reason insist that I use it to access my account. If not does anyone know of a work round other than having to boot into windows. Ta

---

### Post by bapoumba on 2014-04-09
May be you could try a user agent switcher to emulate IE in either Firefox or Chromium : 
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)
[https://chrome.google.com/webstore/detail/user-agent-switcher/lkmofgnohbedopheiphabfhfjgkhfcgf?hl=en](https://chrome.google.com/webstore/detail/user-agent-switcher/lkmofgnohbedopheiphabfhfjgkhfcgf?hl=en)

---

### Post by BBQdave on 2014-04-09
> **robbiejormerod said:**
> Not that I like IE or anything but British Gas for some reason insist that I use it to access my account.

Odd that they would require IE :confused:

If you are using Firefox, I believe there is a UserAgent Add-on, that will allow you to represent your browser as IE. Usually that's all it takes to access sites requiring IE.

---

### Post by Magnezone150 on 2014-04-09
Try Emulating at as said with Firefox and Chrome or there is always the option of using "PlayonLinux" and Wine to run IE on Ubuntu.
Or Test out a totally different browser to see if one will work with that site.

---

### Post by robbiejormerod on 2014-04-09
> **BBQdave said:**
> Odd that they would require IE :confused:

MMMM I thought that too, but they do. :rolleyes:
Anyhows thanks for the advice I'll give it a try when I get back in front of the computer

---

### Post by Mark Phelps on 2014-04-09
>  there is always the option of using "PlayonLinux" and Wine to run IE on Ubuntu.

Not really ...

The latest IE version that POL and Wine install, as far as I know, is version 8! 

And, nearly everyone that uses IE daily uses 10, or those running Win8, ver 11.

While IE 8 might work with the sites you need, more likely, it won't.

And, from what I recall using the IE add-on in FireFox in Windows, it doesn't work without IE in the mix.

---

### Post by monkeybrain20122 on 2014-04-09
> **Mark Phelps said:**
> Not really ...

The latest IE version that POL and Wine install, as far as I know, is version 8! 

And, nearly everyone that uses IE daily uses 10, or those running Win8, ver 11.
.

I doubt that a company that still requires IE would ask for the latest of anything. Sounds like their IT department is still living in 2004.

---

### Post by monkeybrain20122 on 2014-04-09
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/)
This should work.

---

### Post by robbiejormerod on 2014-04-10
> **bapoumba said:**
> May be you could try a user agent switcher to emulate IE in either Firefox or Chromium : 
[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)
[https://chrome.google.com/webstore/detail/user-agent-switcher/lkmofgnohbedopheiphabfhfjgkhfcgf?hl=en](https://chrome.google.com/webstore/detail/user-agent-switcher/lkmofgnohbedopheiphabfhfjgkhfcgf?hl=en)
Thanks, the Chromium emulator works a treat.
 But now the *@%*%*@$ want me to install Activex. From what I can gather from looking around other posts this just isn't possible, but the info I have found is a couple of years old now, anyone know of any new developments that could get around this.
I shall be sending a strongly worded email to British Gas in the meantime. :mad:

---

### Post by coffeecat on 2014-04-10
> **robbiejormerod said:**
> British Gas for some reason insist that I use it to access my account. 

Why do you think that? I have no problem accessing my British Gas account using Firefox in Ubuntu. No user agent switcher. I just log in and use the account.

---

### Post by robbiejormerod on 2014-04-10
Without emulator 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=251897&stc=1&thumb=1&d=1397136675[/IMG]
With emulator
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=251898&stc=1&thumb=1&d=1397136691[/IMG]

---

### Post by pqwoerituytrueiwoq on 2014-04-10
that honestly looks more like a OS filter than a browser filter on the 1st screenshot
i ran into one like that helping my mom do job applications
but if they want you to use activex i would rather find a alternate company to do business with
i don't want to give some website access to my entire computer

you could use virtualbox to run windows, you would need a windows disk or iso file
[http://www.w7forums.com/threads/official-windows-7-sp1-iso-image-downloads.12325/](http://www.w7forums.com/threads/official-windows-7-sp1-iso-image-downloads.12325/)
you can run windows as a trial for a month in a virtualbox
there is a run command to extend it up to 3 months

---

### Post by coffeecat on 2014-04-10
Have a look at the URLs in the screenshots you posted. That's not British Gas that is demanding that you use Internet Explorer - that is paypoint.com. That doesn't help you with your original problem because it looks as though BG is employing paypoint to collect internet topup payments. As I said - I have no problem with my online account with BG but I don't have a pay as you go contract with them so my internet account dealings are entirely with the energy company, not a subcontractor who is disadvantaging non-Windows users. 

Although this does seem to be a limitation of paypoint.com, BG does acknowledge the shortcoming:

[http://www.britishgas.co.uk/help-and-advice/Pay-As-You-Go-Energy/Home-Energy-Top-Up/Setting-up-Home-Energy-Top-Up/What-do-I-need-to-use-Home-Energy-Top-up.html](http://www.britishgas.co.uk/help-and-advice/Pay-As-You-Go-Energy/Home-Energy-Top-Up/Setting-up-Home-Energy-Top-Up/What-do-I-need-to-use-Home-Energy-Top-up.html)

> The Home Energy Top Up service is compatible with Internet Explorer 7, 8, 9, 10 & 11, so if you are using an alternative browser the system will not work. 

You're not just limited to one browser, but one family of operating systems. It would seem that Apple users would be similarly affected.

The reason I mention this is that if you go with a different energy company, which is one of pqwoerituytrueiwoq's suggestions, you would need to check that they don't use paypoint too for a similar energy contract. You'll run into the same problem.

Sorry I can't help further and good luck with solving this.

---

### Post by Mark Phelps on 2014-04-10
> But now the *@%*%*@$ want me to install Activex. From what I can gather from looking around other posts this just isn't possible

That's correct -- it's not possible.

---

### Post by vasa1 on 2014-04-10
OP, as you see from coffeecat's posts, there's no way to get around this issue unless BG/Paypoint fix it themselves. Just writing to BG may not work. Perhaps, a name-and-shame campaign in the media is needed.

---

### Post by robbiejormerod on 2014-04-13
Thanks everyone for your input, I've marked this as solved. Not exactly the way I was hoping for. I've installed a ten year old version on vista on a 150Gb hard drive I had knocking around and just change boot order in BIOS when I need to use it. Not the most eloquent work around but it keeps things neat. Vasa1 is right not just about this but the general lack of support for Linux, it up to us as users to get on to companies that don't offer Linux support and let them know we aren't going to be using their products. If enough people start doing this they will start to listen.

---

### Post by monkeybrain20122 on 2014-04-13
> **robbiejormerod said:**
> Vasa1 is right not just about this but the general lack of support for Linux, it up to us as users to get on to companies that don't offer Linux support and let them know we aren't going to be using their products. If enough people start doing this they will start to listen.

Well it doesn't work for Mac either so these people are just stupid and out of touch. I wouldn't do business with them if I don't have to.

---

