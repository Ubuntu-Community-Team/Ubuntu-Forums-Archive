---
title: "Firefox questions - freezing- search"
date: 2022-03-28
forum: General Help
---

### Post by bjngchn on 2022-03-28
There is a search area in my firefox, which I can't remove, 
still my address bar is also used for search, meaning my url visits  are sent to "my favorite search engine". 
How can I remove this from happening. 
Address bar is for address, not for search engine search. (but it is great for bookmark search)
 .......................... 
Second question: Any site  I visit on Firefox can freeze my computer. 
Not only firefox, but the whole computer freezes. 
Alt+F4 doesn't work. I think this is intentional.
 Is there a way to avoid  this, or get rid of this when it happens? 
Even if I disconnect from internet, whatever script they have, 
they can freeze the computer and it  seems impossible to get rid of it. 

(Andwho knows, in new computers, since battery is not removable either, 
it would be immpossible to turn computer off.
 ................ 
If it is so easy to crush a linux computer, why such  things don't happen on  purely evil closed source smartphones? 
Where is the superiority of linux in security and privacy sense?  .... thanks in advance.

---

### Post by ajgreeny on 2022-03-28
Which version of Ubuntu and also of firefox are you using, and is the system fully updated?
What spec hardware do you have?

Please show us the output of terminal command **inxi -Fzx** as a start which will tell us a lot more about your system.

---

### Post by Impavidus on 2022-03-28
If what you type in the address bar looks like an address or something from your bookmarks, Firefox will visit it. Only in the other cases it will be send to your favourite search engine.

Have you got any particular reason to believe those freezes are intentional?

---

### Post by bjngchn on 2022-03-28
All are new. Operating system, 20 plus something kubuntu, firefox is also new, and everything is updated even if I don't want them to. 
These are general questions, not about me, or my computer. Such problems always existed. and still exist.

---

### Post by dragonfly41 on 2022-03-28
You should attempt to narrow down the list of clues ..

If you create a fresh firefox profile (with no changes such as adding extensions) do you still experience freeze?

Run .. firefox --help
to see how to use Profile Manager

---

### Post by ajgreeny on 2022-03-28
Saying ***20 plus something kubuntu, firefox is also new*** is not very helpful and could mean anything from 20.04, 20.10, 21.04, 21.10 and even 22.04 if you have already tried the beta version of the LTS still to be released next month.

And as I said before, please show us the output of terminal command ***inxi -Fzx *** as that will tell us a lot more about your OS and the hardware on which you run it.

---

### Post by #&amp;thj^% on 2022-03-28
> **bjngchn said:**
> There is a search area in my firefox, which I can't remove, 
still my address bar is also used for search, meaning my url visits  are sent to "my favorite search engine". 
How can I remove this from happening. 
Address bar is for address, not for search engine search. (but it is great for bookmark search)

You've made it clear the other questions besides the above, have no value to yourself, but for the above quote^^^
Enter this in the address bar: about: Preferences#search ###remove the space between ": Pr" sorry forum software
You will see only this,
> Search
Search Bar
Use the address bar for search and navigation
Add search bar in toolbar
FWIW: i find it very hard to crush a linux computer
Here's a hack for the old address/url bar/window
do this please :

Type in the address bar "about:config" and press Enter.
(ignore the warning)

Type in the search bar and look for the preference :
[list]
1 at a time
[*]browser.urlbar.openViewOnFocus

[*]browser.urlbar.update1

[*]browser.urlbar.update1.interventions

[*]browser.urlbar.update1.searchTips[/list]
and set its value to   false

Do the same with all these preferences. 

Then close and restart Firefox.

---

### Post by ajgreeny on 2022-03-30
Hey, ifallen.

Just out of interest I looked in ***about:config*** and not one of those four items you listed are present

[B][I]browser.urlbar.openViewOnFocus
browser.urlbar.update1
browser.urlbar.update1.interventions
browser.urlbar.update1.searchTips[/I][/B]

They could be created and then given a value depending on the type chosen, but are not apparently present by default, so I wonder, which FF version are you using?

@bjngchn 

You can add a separate search box to the toolbar by right clicking in the toolbar -> Customise Toolbar then drag the Search Box to where you want it to be, either right beside the address box or elsewhere if you prefer.
Unfortunately I don't think that stops the address box from searching in the way that you wish, though there may be other ways to stop this happening that I'm not aware of. Maybe simply choosing History instead of a search engine name when you click on the search icon in the address box will do what you want.

---

### Post by #&amp;thj^% on 2022-03-30
> **ajgreeny said:**
> Hey, ifallen.

Just out of interest I looked in ***about:config*** and not one of those four items you listed are present

[B][I]browser.urlbar.openViewOnFocus
browser.urlbar.update1
browser.urlbar.update1.interventions
browser.urlbar.update1.searchTips[/I][/B]

They could be created and then given a value depending on the type chosen, but are not apparently present by default, so I wonder, which FF version are you using?


What version are you using? 
mine:
```
 apt policy firefox
firefox:
  Installed: 98.0.2+build1-0ubuntu0.21.10.1
  Candidate: 98.0.2+build1-0ubuntu0.21.10.1
  Version table:
 *** 98.0.2+build1-0ubuntu0.21.10.1 500
        500 http://archive.ubuntu.com/ubuntu impish-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu impish-security/main amd64 Packages
        100 /var/lib/dpkg/status
     93.0+build1-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu impish/main amd64 Packages

```
Best seen in screenshot or two.

---

### Post by ajgreeny on 2022-03-31
Same version of FF here except mine is still for 20.04.

But surely the + at the right hand end means that the item does not already exist and you are creating it as a new config item?

---

### Post by #&amp;thj^% on 2022-03-31
> **ajgreeny said:**
> Same version of FF here except mine is still for 20.04.

But surely the + at the right hand end means that the item does not already exist and you are creating it as a new config item?

I get your logic there, and that makes sense. but it was already there, but deactivated or activated depending on your view. :)
just type in the **about:config **part this: "**browser.urlbar**" you'll see a long list of options, some active/enabled others are options for a knowing user to tweak as needed. So yes it was always present, just not set.

---

### Post by ajgreeny on 2022-03-31
> **1fallen said:**
> I get your logic there, and that makes sense. but it was already there, but deactivated or activated depending on your view. :)
just type in the **about:config **part this: "**browser.urlbar**" you'll see a long list of options, some active/enabled others are options for a knowing user to tweak as needed. So yes it was always present, just not set.
Yes, there's a long list of options starting ***browser.urlbar*** but none of the specific ones you mention as far as I can see.
However I do already have a 
***browser.urlbar.searchSuggestionsChoice***
which is set to false but my address bar does search using google or duckduckgo depending on my search engine choice in FF preferences, and I have not found a way to stop that.  It does not bother me at all that a search is done that way from the address bar.

---

### Post by #&amp;thj^% on 2022-03-31
> **ajgreeny said:**
> but my address bar does search using google or duckduckgo depending on my search engine choice in FF preferences, and I have not found a way to stop that.  It does not bother me at all that a search is done that way from the address bar.
Ahhh ok then use in
**about:config**
Search "**browser.urlbar.suggest.searches"** and change it to **false **(Do this Only if you want to disable suggesions)
Search "**keyword.enabled**" and change it to **false**
Search "**browser.fixup.alternate.enabled**" and change it to **false **
I clearly left that out of my first suggestions.
will you try that? and confirm. :)
EDIT I need to add after restarting firefox.

---

