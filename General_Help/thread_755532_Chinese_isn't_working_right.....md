---
title: "Chinese isn't working right...."
date: 2008-04-14
forum: General Help
---

### Post by rmaguir on 2008-04-14
Whenever I type in Chinese, many (not all) of the words come up as squares with (I guess) unicode numbers in them.  I've downloaded everything I can find to make sure I have all of the fonts necessary, but nothing's changed.

---

### Post by phidia on 2008-04-14
What application is this happening in? I'm not sure but have you looked in System>Appearance>Fonts and made sure the font is available?

---

### Post by rmaguir on 2008-04-14
> **phidia said:**
> What application is this happening in? I'm not sure but have you looked in System>Appearance>Fonts and made sure the font is available?

When I go into System>Appearance>Fonts, what's the name of the font I'm looking for?  It doesn't just say "traditional Chinese" does it?

BTW, I forgot to mention that I am using Traditional Chinese and not simplified, if that makes much of a difference.

---

### Post by rmaguir on 2008-04-14
> **phidia said:**
> What application is this happening in? I'm not sure but have you looked in System>Appearance>Fonts and made sure the font is available?

Forgot to mention that it's happening primarily in, at least, Firefox and OpenOffice...

---

### Post by IcemanV9 on 2008-04-15
Check to see if your language is supported in System > Admin > Language Support.

---

### Post by rmaguir on 2008-04-15
Yeah.  It is.

---

### Post by phidia on 2008-04-15
> **rmaguir said:**
> Forgot to mention that it's happening primarily in, at least, Firefox and OpenOffice...

Does OOffice have separate font settings? You may need to search the OpenOffice forums? [Here]("http://projects.openoffice.org/native-lang.html") or [here]("http://support.openoffice.org/index.html")

---

### Post by rmaguir on 2008-04-16
but, even if I fixed it in Office, wouldn't I still have the problem in Firefox?  I use Chinese a lot more in Firefox than I do in Office....

---

### Post by IcemanV9 on 2008-04-17
Ok. It is supported in system > admin > language support. In the terminal, type ...
```
locale
```
If it is not your default language [zh_CN.UTF-8], then type ...
```
sudo dpkg-reconfigure locales
```
If you want to change the keyboard layout for Chinese, then modify one line in xorg.conf. ```
Option      "XkbLayout" "us"
```
Change "us" to "zh" And, restart the X.

---

### Post by seshomaru samma on 2008-04-24
Sounds like a font problem
probably the systme fonts don't have all the traditional characters in them
I would change the system fonts to something Chinese 
Also do 
```
sudo apt-cache search chinese
```
it will give you a list of pacakges related to Chinese 
install all the fonts it gives you

---

### Post by lancest on 2008-05-07
Some of the Chinese characters don't print in my Open Office writer & calc documents. Chinese is enabled. (Some print some don't) Using scim.

---

### Post by rmaguir on 2008-05-07
Someone recently told me that their Chinese was working fine, only to then find out that they had set their regional locale to Chinese.  Upon reseting said locale, their Chinese no longer worked.  

Whether or not that's the ticket, I don't know, because I haven't tried.

---

