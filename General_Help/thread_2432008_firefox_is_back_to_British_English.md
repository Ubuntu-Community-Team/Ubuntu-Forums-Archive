---
title: "firefox is back to British English"
date: 2019-11-25
forum: General Help
---

### Post by Skaperen on 2019-11-25
firefox is back to British English.  i need to get it to stay on United States English.  what package should i remove so it has no knowledge of British English at all?

---

### Post by #&amp;thj^% on 2019-11-26
The first thing I would do is enter in the URL: "about:config"
Then search for "intl.accept_languages" and make sure it is set to "en-us,en"

The alternative is to install a build of Firefox already localized in your preferred language. But, once again, they&#8217;re not so easy to find.
Found here: [https://www.mozilla.org/en-US/firefox/all/#product-desktop-release](https://www.mozilla.org/en-US/firefox/all/#product-desktop-release)
Once set as default it should not change.

---

### Post by Skaperen on 2019-11-26
hmmm.  it is already set to "en-US, en".  yet, it is still recommending that i spell "color" as "colour".  should i remove the ", en" and see what happens?

---

### Post by #&amp;thj^% on 2019-11-26
> **Skaperen said:**
> hmmm.  it is already set to "en-US, en".  yet, it is still recommending that i spell "color" as "colour".  should i remove the ", en" and see what happens?
[s]Nope I wouldn't, and yep I see that too (colour), but other than that, it's all "en-US" on my side.
Probably on Ubuntu's Mozilla's team side to fix. (British based you know ;))[/s]
Try the link I provided to see if there are any differences.
I just changed the "en-US, en" to "en-US" and yes there is a change on the spelling. :(
And color and colour now show as seen in my screenshot.

---

### Post by Skaperen on 2019-11-27
in the user i had the issue, i did add to dictionary so i can't test it there.  same thing here in user "forums" where i read ubuntuforums.org.  i need to find a user where i didn't do that, or a way to delete that dictionary add-on.

---

### Post by uRock on 2019-11-27
I had this issue many moons ago. I went through every setting I could find. I ended up creating a new ***.mozilla*** folder.

---

### Post by ajgreeny on 2019-11-27
Have a look in **Tools ->Add-Ons ->Dictionaries** and see which dictionaries are installed.  If the British English version is shown you can either disable it or possibly delete it completely but you may need to add the US English dictionary if not already installed.

---

### Post by Skaperen on 2019-11-28
> **uRock said:**
> I had this issue many moons ago. I went through every setting I could find. I ended up creating a new ***.mozilla*** folder.


good thought.  so i logged in a user i rarely use and all its files are at least 3 months old (except the ones just now touched from being logged in).  i fired up firefox and it looked like it had never been run under that user.  the problem did not exist there.  so i quit firefox and removed [COLOR=#0000cd][FONT=courier new]**~/.mozilla**[/FONT][/COLOR] and started firefox, again.  same thing.  so, i'm unsure what's going on at this point.

---

### Post by Skaperen on 2019-11-28
> **ajgreeny said:**
> Have a look in **Tools ->Add-Ons ->Dictionaries** and see which dictionaries are installed.  If the British English version is shown you can either disable it or possibly delete it completely but you may need to add the US English dictionary if not already installed.
for the other user it did have just Canadian and British.  for user "forums" (here where i am typing this post) it has United States and the two major dialects of Norwegian (what i want).  but i see no means to disable or delete.  not even to install (or does that need to be apt-get?).

---

### Post by #&amp;thj^% on 2019-11-28
Just as ajgreeny advised Tools ->Add-Ons ->Dictionaries There is a search bar available addons. See screenshot.
After you add one if necessary, you can make the needed changes off to the right of any addon.

---

### Post by Skaperen on 2019-11-28
Tools->Add-Ons does not have "Dictionaries" as a choice for the user with a problem (user skaperen).  user "forums" does have "Dictionaries".  what's up with this difference? 

see these 2 1920x1080 PNG snapshots:
[http://ipal.net/ubuntu/201911281731271568690776.png](http://ipal.net/ubuntu/201911281731271568690776.png)
[http://ipal.net/ubuntu/201911281743361560704946.png](http://ipal.net/ubuntu/201911281743361560704946.png)

---

