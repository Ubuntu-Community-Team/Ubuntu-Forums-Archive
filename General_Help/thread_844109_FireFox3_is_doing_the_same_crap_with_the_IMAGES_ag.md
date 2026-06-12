---
title: "FireFox3 is doing the same crap with the IMAGES again :("
date: 2008-06-29
forum: General Help
---

### Post by heatblazer on 2008-06-29
Take a look what happens when I try to google search IMAGES in FireFox3. Why is this happening :( How can I fix it? 
 It`s a matter of time before I got frustrated and go to FF2 or Epiphany or Konqueror...

---

### Post by marshall.robert on 2008-06-29
its a long shot, but ive noticed that ff3 doesnt load css properly the first time round on some paged, so i do a full refresh with CTRL+F5 to get all content, try that and see if that works

---

### Post by dentaku65 on 2008-06-29
Silly question: do you have enabled in the preferences under content "Load images automatically"?

---

### Post by nikgare on 2008-06-29
I sometimes got something similar to this but not quite as bad.  The problem I was having was with the dns server from my isp being a bit crap, so I switched to other dns servers, and solved the problem for me.

---

### Post by heatblazer on 2008-06-29
> **dentaku65 said:**
> Silly question: do you have enabled in the preferences under content "Load images automatically"?

Yes. It was normal. But when I right click and tried to open a link in a new tab it screwed up like this :( It has happened again :( The previous time I just deleted the .Mozilla directory from HOME and set everything up again... This time I`ll just go with Ephipany...  BAN that Fox!

---

### Post by stinger30au on 2008-06-29
> **heatblazer said:**
> Yes. It was normal. But when I right click and tried to open a link in a new tab it screwed up like this :( It has happened again :( The previous time I just deleted the .Mozilla directory from HOME and set everything up again... This time I`ll just go with Ephipany...  BAN that Fox!


file it in the mozilla bug reports as well so i can be looked at.... they may already have a fix for it


[https://bugzilla.mozilla.org/](https://bugzilla.mozilla.org/)

---

### Post by heatblazer on 2008-06-30
I sent a request to bugzilla. Hope that they do something about that crash. It`s an incredibly annoying problem, that should be fixed, or more users are getting frustrated.

---

### Post by heatblazer on 2008-06-30
I tried Ctrl+F5 no difference... I hope that Bugzilla are reading their mails... this is very very frustrating problem... I hate it and this time I won`t reenter everything back, I`ll just try Epiphany if they don`t fix it.

---

### Post by aashay on 2008-06-30
Bit of a longshot but check if browser.display.show_image_placeholders is set to True in about:config

---

### Post by SIXAXIS on 2008-06-30
I had that problem while viewing Google images on my PSP a while ago, but it just kind of went away. It may be something on Google's part or maybe Firefox is messing it up.

---

### Post by davidpbrown on 2008-06-30
For a while now there's been a FF bug that's actioning random right-click choices when user right-clicks and I've seen it do what you're experiencing

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313)
is Master to a bunch of these frustrated because the cause is apparently not obvious.

Edit::Preferences::Content::Load images automatically::Exceptions and remove sites from the list might help.

---

### Post by heatblazer on 2008-06-30
> **aashay said:**
> Bit of a longshot but check if browser.display.show_image_placeholders is set to True in about:config

I beg your pardon, what do you propose? Can you describe it more in-deep?

---

### Post by aashay on 2008-06-30
type in about:config in the address bar. You will be presented with a list of attributes. Scroll through (or filter) for the browser.display.show_image_placeholders one and check if it is true.

---

### Post by heatblazer on 2008-06-30
I checked it... it`s "TRUE".. :(

---

### Post by heatblazer on 2008-06-30
> **aashay said:**
> type in about:config in the address bar. You will be presented with a list of attributes. Scroll through (or filter) for the browser.display.show_image_placeholders one and check if it is true.

Tried it... Still that crap... Man I am desperate... :(

---

### Post by nikgare on 2008-06-30
Does this happen for all users, newly created users or just your account?

---

### Post by heatblazer on 2008-06-30
Can you tell me how to import all FF3 data into Epiphany at least?

---

### Post by heatblazer on 2008-06-30
> **nikgare said:**
> Does this happen for all users, newly created users or just your account?

In all accounts and sessions (KDE and GNOME), however Epiphany (GECKO) is working just fine.

---

### Post by dentaku65 on 2008-07-01
> **heatblazer said:**
> Tried it... Still that crap... Man I am desperate... :(

Did you tried to create an empty profile? Close FF3, then

```
mv ~/.mozilla ~/.mozilla.SAVE
```

then reopen FF3; if is works should be something in your configuration (some plugin or extension)

---

### Post by heatblazer on 2008-07-01
> **dentaku65 said:**
> Did you tried to create an empty profile? Close FF3, then

```
mv ~/.mozilla ~/.mozilla.SAVE
```

then reopen FF3; if is works should be something in your configuration (some plugin or extension)

What was that command?! Everything vanished! Yes it opened the images but my browser is set to default and no bookmarks?!

---

### Post by heatblazer on 2008-07-01
Now tell me how to fix it! It was a bad command!

---

### Post by polki@mac.com on 2008-07-01
This brings it back:

mv ~/.mozilla.SAVE ~/.mozilla

---

### Post by meganox on 2008-07-01
It was a good command, it backed up your firefox profile to  ~/.mozilla.SAVE

Open a file browser window in your home folder and select "show hidden files" from the view menu or press ctrl-h and you will see it.  

Firefox created a new .mozilla folder and a default profile in it.  Since it's now working, you can be sure something in your old profile was causing the error.

This is the standard way of checking if something is a bug in firefox or if it exists in your extensions or elsewhere in your profile, and is mandatory before submitting a firefox bug.

What you need to do now is move your settings over from ~/.mozilla.SAVE/firefox/<whatever>.default to the new profile in ~/.mozilla/firefox/<whatever>.default.  There is information [here]("http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox") on doing this, as well as general information about profiles in firefox.

I would advise you to move only the places.sqlite file and then to make all your firefox settings manually and install all your extensions again.  Extensions usually will break if moved directly from one profile to another and it is not a good idea to move the preference file if you have had problems.

Was this profile one you were using with firefox2?  I always create a new profile when firefox changes major version numbers.

You can manage multiple firefox profiles and switch between them by hitting Alt-F2 and entering "firefox -profilemanager"

---

### Post by heatblazer on 2008-07-01
???... does not work :( It still gives me a clean install FF...

---

### Post by dentaku65 on 2008-07-01
> **heatblazer said:**
> ???... does not work :( It still gives me a clean install FF...

Did you already use this:

```
mv ~/.mozilla.SAVE ~/.mozilla
```

If you did the mv command, please post the output of this:
```
ls -al ~/.mozilla/firefox
```

**- DON'T DO THE FOLLOWING NOW -**
By knowledge the correct procedure of restore (but if you did already the above command [COLOR="Red"]DON'T DO IT NOW![/COLOR]) was:
```
rm -R ~/.mozilla
```
```
cp -R ~/.mozilla.SAVE ~/.mozilla
```

---

### Post by dentaku65 on 2008-07-01
> **polki@mac.com said:**
> This brings it back:

mv ~/.mozilla.SAVE ~/.mozilla

no, this is wrong using mv in this case cannot preserve a back-up copy

---

