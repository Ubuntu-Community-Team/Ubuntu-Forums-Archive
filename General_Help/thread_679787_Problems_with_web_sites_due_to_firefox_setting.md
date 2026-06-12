---
title: "Problems with web sites due to firefox setting"
date: 2008-01-27
forum: General Help
---

### Post by DugieHowsa on 2008-01-27
Greetings all.  I just wanted everyone to know about an issue I recently came across and how I resolved it.

Starting with Gutsy (7.10), some settings had been changed in Firefox that may be adversely affecting user experience with some web sites.  I had noticed an issue with [www.hotmail.com](www.hotmail.com) and mail.live.com.  Event though they said the supported their "enhanced" features with Firefox 1.5 and up, I was not able to utlize them.  Then I found a post here that recommended the following:

1)  Open the Firefox Browser
2)  in the address bar, type the following to bring up the firefox config page:
     about:config
3)  Search for the following preference name:
     general.useragent.vendor
4)  By Default, it is listed as Ubuntu.  Change it to:
     Firefox

After that, the web sites performed as expected.  Now, I realize this might not solve all problems, but it is just another thing to look at.

---

### Post by seventhc on 2008-01-27
I to have noticed issues unless I use the classic view of their site, same with yahoo mail.
I hope this fixes that too, I'll give it a try.
thanks for the tip. :)

Edit: Looks like it works. :)

---

### Post by sports fan Matt on 2008-01-27
I dont see this anywhere in the about:config menu..Do you need to create a new integer of string?  Also what is the last thing its down from?

---

### Post by seventhc on 2008-01-27
> **sox fan Matt said:**
> I dont see this anywhere in the about:config menu..Do you need to create a new integer of string?  Also what is the last thing its down from?
when your in the config menu you should see a place where you can type, it says filter(like a search) enter       " general.useragent.vendor " there and you'll see the option.

---

### Post by sports fan Matt on 2008-01-27
I see nothing there..how odd..i copied and pasted in the filter and that preference doesnt seem to exist for a strange reason..im running firefox 2.0.0.11

---

### Post by seventhc on 2008-01-27
Thats odd, I'm running the same version...:confused:

---

### Post by sports fan Matt on 2008-01-27
I even went to where it should be and its not..my question why isnt it :(

---

### Post by seventhc on 2008-01-27
The only thing I can think of is if maybe it has to do with installed plug-ins other than that, I have no idea why it wouldn't be there for you.

---

### Post by sports fan Matt on 2008-01-27
the only ones i have are forecastfox enchanced and the yahoo mail notifier plus im using the I safari theme

---

### Post by rmx77 on 2008-01-27
i noticed another error and its with profile sites where when you try to view someones page by clicking their name or picture once it tries to open a program or download something so what i found you do is double click the name or picture from the list and then u can access the page but the other problem is when u get onto a page sometimes firefox wants u to open a file in the html/xml program insted of going back. what can be done to fix this

---

### Post by seventhc on 2008-01-27
> **sox fan Matt said:**
> the only ones i have are forecastfox enchanced and the yahoo mail notifier plus im using the I safari theme
I actually meant maybe certain plugins might create that option, but that doesn't sound to likely. I am really not to sure, if you do find out, please let me know.

---

