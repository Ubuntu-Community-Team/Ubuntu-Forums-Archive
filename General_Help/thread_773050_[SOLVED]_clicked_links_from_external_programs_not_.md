---
title: "[SOLVED] clicked links from external programs not opening"
date: 2008-04-28
forum: General Help
---

### Post by Irishpolyglot on 2008-04-28
Hi! I'm sure this has a very simple solution... Since I upgraded to Hardy any link I click in Pidgin or Evolution etc. doesn't do anything. Anything unrelated to web browsing (like clicking an email link that opens in Evolution) works fine. Everything within Firefox works fine. There were no problems before the upgrade. Any help greatly appreciated :)

---

### Post by kenny1948 on 2008-04-29
I am having the same problem. Made the mistake of installing the upgrade to Hardy last night. Now I cannot answer or read any e'mail because links do not work.:confused:

---

### Post by pro003 on 2008-04-29
Guys, no panic. Remove those icons/shortcuts from panel and go to Applications then add one by one new shortcuts to panel or desktop.

that's because you got plenty of new apps versions in hardy...:popcorn:

---

### Post by Irishpolyglot on 2008-04-29
pro003, you completely misunderstood me. Links to websites do not open, I'm not talking about clicking applications. I want to click a web address in Evolution or Pidgin and have it open in Firefox as it was doing before.
Kenny; I wouldn't say upgrading to Hardy was a mistake because of this... why don't you just select the link and copy and paste it ;) It doesn't mean you "cannot answer or read emails".
But I'd still appreciate an insight into why this is happening and how to get around it. It's not a serious issue, but it is quite annoying...
Cheers

---

### Post by pro003 on 2008-04-29
> pro003, you completely misunderstood me. Links to websites do not open, I'm not talking about clicking applications. I want to click a web address in Evolution or Pidgin and have it open in Firefox as it was doing before.

I get it. Now, I had this problem to. This is because you are still using Firefox 2.xx. And if you uninstallit and install Firefox 3 beta, you'll have you're links from email opened in browser..which is - Firefox 3.

Sorry for misunderstanding you :popcorn:

---

### Post by Irishpolyglot on 2008-04-29
No, this isn't the problem. After I originally installed Firefox 3.0b in Gutsy it was set as the default and all links I clicked in other programs opened in 3.0b. I just had a look in Synaptic and Firefox 2 is not installed so I imagine it was uninstalled in the upgrade. Perhaps I have no default browser? How can I set it to be Firefox 3.0b or does anyone have any other suggestions?
Thanks

---

### Post by pro003 on 2008-04-29
try this in your terminal:

```
export BROWSER="firefox"
```

let me know if it works!

---

### Post by Irishpolyglot on 2008-04-29
Thanks for continue to try ;) Very much appreciated!
I just ran that code and it's made no difference. Any other suggestions?

---

### Post by pro003 on 2008-04-29
1. Go to "System -> Preferences -> Preferred Applications".


2. Select "Custom Web Browser", and type "firefox %s" in the box ("mozilla %s" for Mozilla). Note that a symlink of the "firefox" or the "mozilla" script must be placed in one of the default PATHs (for example, a symlink of the "firefox" script to "/usr/bin/" is common). 

:guitar:

---

### Post by yaknowwat on 2008-04-29
System > Preferences > Preferred Applications

Set it to firefox

If that does not work

Open synaptic and reinstall firefox 3 and try again after that it should work.

chances are when uninstalling firefox 2 it unregistered your default web browser.

---

### Post by Irishpolyglot on 2008-04-29
Yes, that's done it! :) Many thanks as always! Your explanation makes sense.

---

### Post by pro003 on 2008-04-29
> **Irishpolyglot said:**
> Yes, that's done it! :) Many thanks as always! Your explanation makes sense.

you're welcome :popcorn:

---

### Post by yaknowwat on 2008-04-29
> **Irishpolyglot said:**
> Yes, that's done it! :) Many thanks as always! Your explanation makes sense.

Glad we could help.

---

### Post by blumnday99 on 2008-05-12
Is there anyway to fix Hardy so it'll use FireFox 2?  A lot of my extensions aren't compatible with Firefox 3 Beta...I've changed the preferred application to firefox-2.  Now when I click an external link, it opens Firefox, but doesn't load the appropriate website.  Is there an extension I have to add to the end of firefox-2 to tell it to load an external hyperlink?

Mark

---

### Post by pro003 on 2008-05-12
yes you can get back firefox 2... just go to 

System > Administration > Synaptic package manager 


then search word : firefox, but under "name"... not description and you can mark for total removal of firefox 3 and after that check version two for installation, you can do it at once if you want to...

then...

go to System > Preferences > Prefered Applications end select firefox for default - you may type command of firefox as well... sheck it out in properties when you place it on desktop or panel...

that's pretty much it :popcorn:

---

### Post by blumnday99 on 2008-05-13
> **pro003 said:**
> yes you can get back firefox 2... just go to 

System > Administration > Synaptic package manager 


then search word : firefox, but under "name"... not description and you can mark for total removal of firefox 3 and after that check version two for installation, you can do it at once if you want to...

then...

go to System > Preferences > Prefered Applications end select firefox for default - you may type command of firefox as well... sheck it out in properties when you place it on desktop or panel...

that's pretty much it :popcorn:

Already did that....Firefox 2 still isn't showing up under the Preferred Applications-->Web Browser.  Right now I'm launching it with the custom command firefox-2.  When I click an external link, it opens firefox but doesn't open any pages.  Removing and reinstalling firefox via terminal or synaptic doesn't make FireFox-2 appear in the Preferred Applications window.

---

### Post by blumnday99 on 2008-05-13
> **blumnday99 said:**
> Already did that....Firefox 2 still isn't showing up under the Preferred Applications-->Web Browser.  Right now I'm launching it with the custom command firefox-2.  When I click an external link, it opens firefox but doesn't open any pages.  Removing and reinstalling firefox via terminal or synaptic doesn't make FireFox-2 appear in the Preferred Applications window.

Figured it out....using firefox-2 as a custom command and then adding "%s" apparently tells firefox to open with an external hyperlink....so the complete custome command in preferred applications should be 

firefox-2 "%s"

---

### Post by pro003 on 2008-05-13
> using firefox-2 as a custom command and then adding "%s" apparently tells firefox to open with an external hyperlink....so the complete custome command in preferred applications should be

firefox-2 "%s"


you just took my words i was going to put here :-)

anyway, glad you made it

---

