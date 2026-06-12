---
title: "Flash covers up other website content"
date: 2007-11-04
forum: General Help
---

### Post by Dr_Snapid on 2007-11-04
Does anyone know how to stop Flash elements in websites from being always on top?

Whenever I go to a website (like asus.com) where the menus should appear over the top of a flash element, the menu actually appears UNDER the flash element in Ubuntu. The flash element sits on top of the menu so I cant use the menu!

This have been ongoing for quite some time. Is there a workaround?

You can see the issue here:
[http://www.asus.com/index.aspx](http://www.asus.com/index.aspx)

---

### Post by stchman on 2007-11-04
> **Dr_Snapid said:**
> Does anyone know how to stop Flash elements in websites from being always on top?

Whenever I go to a website (like asus.com) where the menus should appear over the top of a flash element, the menu actually appears UNDER the flash element in Ubuntu. The flash element sits on top of the menu so I cant use the menu!

This have been ongoing for quite some time. Is there a workaround?

You can see the issue here:
[http://www.asus.com/index.aspx](http://www.asus.com/index.aspx)

It is a bug in Flash 9.

---

### Post by michaelzap on 2007-11-04
> **stchman said:**
> It is a bug in Flash 9.

And a very annoying one at that. The Adobe folks apparently have said that it's because no Linux browser supports wmode transparent, but I suspect that's a cop out. I really hope either Adobe or Mozilla fixes this soon.

---

### Post by FuturePilot on 2007-11-04
> **michaelzap said:**
> And a very annoying one at that. The Adobe folks apparently have said that it's because no Linux browser supports wmode transparent, but I suspect that's a cop out. I really hope either Adobe or Mozilla fixes this soon.

Yes, I have also heard that. It's kind of hard to believe that the Windows version of Firefox supports this but the Linux version doesn't.[-(

---

### Post by stchman on 2007-11-05
> **michaelzap said:**
> And a very annoying one at that. The Adobe folks apparently have said that it's because no Linux browser supports wmode transparent, but I suspect that's a cop out. I really hope either Adobe or Mozilla fixes this soon.

Yes, it is a cop out on their part.  If Adobe wanted to fix the problem they could.  They figure it is just a bunch of Linux geeks so it does not really matter.

There are numerous Flash enabled websites out there so it is getting bad.

---

### Post by Seq on 2007-11-05
> **stchman said:**
> There are numerous Flash **dis**abled websites out there so it is getting bad. Fixed that for you ;) Try using Linux on non-intel (like PPC).

Can you post an example link? I use flashblock extension on my intel machine, and can check if this happens with 'blocked' flash content as well. It might be a decent workaround for the moment.

**EDIT**: Duh, example in the first post. I'll check when I get home and post results here.

---

### Post by stchman on 2007-11-05
> **Seq said:**
> Fixed that for you ;) Try using Linux on non-intel (like PPC).

Can you post an example link? I use flashblock extension on my intel machine, and can check if this happens with 'blocked' flash content as well. It might be a decent workaround for the moment.

**EDIT**: Duh, example in the first post. I'll check when I get home and post results here.

Yes I know that you can disable or uninstall Flash, that also removes functionality as well.  It would be better just to get Flash fixed fro Linux.

---

### Post by Seq on 2007-11-06
> **stchman said:**
> Yes I know that you can disable or uninstall Flash, that also removes functionality as well.  It would be better just to get Flash fixed fro Linux.

If you have flashblock installed, you can still access the menu properly.

Flashblock actually inserts a placeholder in-place of flash files. If you click the place-holder, the flash loads. It is actually very handy.

---

### Post by Dr_Snapid on 2007-11-29
Interesting approach. Id rather have it work properly though. Thankfully, Asus website allows you to access those hidden items another way so i wasnt blocked from using them, but it was annoying. Had there been no other way to access what i needed, flashblock might have helped.

---

### Post by mysticrider92 on 2007-11-29
The Asus site works fine for me, on 32 bit Arch Linux with Adobe flash (gnash did not work for me on Ubuntu, so I am just using the binary).. 

Something that might help is ad block plus. It puts a little tab above each flash element in a site. If one is not working right, just block it. Once you get what you want, you can un block it by removing it from the blocked items list.

[edit] Okay, now the flash items cover the menus. Why can't people just learn the amazing powers of .gif and Ajax...

---

### Post by Astinsan on 2008-02-28
I am still seeing this issue now... today.  How does firefox deal with embedded objects? Maybe there is a hack in there...Just a thought... I have been using ad blocker but not all flash is worthless.  a lot of news sites are using it now and unfortunately flash video feeds are what I am going there for.  Haven't tried gnash though.

---

### Post by Ron F. on 2008-03-06
> **Astinsan said:**
> I am still seeing this issue now... today.  How does firefox deal with embedded objects? Maybe there is a hack in there...Just a thought... I have been using ad blocker but not all flash is worthless.  a lot of news sites are using it now and unfortunately flash video feeds are what I am going there for.  Haven't tried gnash though.

I am running a nightly-build of Firefox 3.0b4pre on my Ubuntu 7.10 machine - and the problem remains. The same problem also exists in the latest version of Opera.

-Ron

---

### Post by michaelzap on 2008-03-06
And yet it doesn't happen in IE (using IEs4Linux), so it can't be an unresolvable problem...

---

### Post by Sir Rodness on 2008-05-16
Man I was just starting to enjoy Linux. But this flash bug is driving me nuts. I go to NBA.com a lot to check info and the menus are always hidden by the flash on the page. Currently my work around is to use VirtualBox with in Linux and install Windows and switch to seemless mode to use Firefox in there. (VirtualBox is pretty cool I must say).I do hope they fix this flash issue soon.

---

### Post by zedstrange on 2008-06-21
You think you got problems. I did an update a few days ago, and now almost every website I visit has the Placeholder instead of the flash content.

and flashblock is not installed.

Its annoying.  I wouldnt mind if i changed something, cos then i could reverse it but this doesnt make sense.

---

