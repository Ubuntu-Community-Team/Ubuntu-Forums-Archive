---
title: "firefox: delete profile"
date: 2020-03-08
forum: General Help
---

### Post by Skaperen on 2020-03-08
i'm trying to delete a few profiles in Firefox that i have created and later decided that i do not want to use.  but i cannot get to that menu that had the delete button.

---

### Post by ipv on 2020-03-08
```
about:profiles
```

on a blank page in firefox type the above in the address bar that should give you all the profiles listed.

barring the current one in use you can remove all the rest.

hope this helps you.

---

### Post by Skaperen on 2020-03-09
i don't want to remove all the rest, just a few of them.

---

### Post by CelticWarrior on 2020-03-09
> **Skaperen said:**
> i don't want to remove all the rest, just a few of them.

Remove only those you want to remove :P
The only one you can't remove is the one in use at the time.

---

### Post by Skaperen on 2020-03-09
s/all/any/

i thought **ipv** meant that there would be a button to delete all profile except the current one.  i take wording literally.

---

### Post by kesetyan on 2020-03-10
Open a terminal and type 'firefox -ProfileManager' *without the speech marks*

You should then get a window that shows a list of your profiles with buttons to the left for 'Create Profile', 'Rename Profile' and 'Delete Profile'.  Highlight the profile in question and click the appropriate button.

---

### Post by monkeybrain20122 on 2020-03-10
Close Firefox, open the file manager. Show hidden files. Go to the folder .Mozilla. Inside there is a subfolder called "firefox", inside there are numerous folders for the profiles, just delete those you want to delete (or you can rename them. In case something goes wrong just rename them back)

---

### Post by walts48 on 2020-03-12
> **monkeybrain20122 said:**
> Close Firefox, open the file manager. Show hidden files. Go to the folder .Mozilla. Inside there is a subfolder called "firefox", inside there are numerous folders for the profiles, just delete those you want to delete (or you can rename them. In case something goes wrong just rename them back)

Does this method update the profiles.ini file, or does it have to be opened in a text editor and edited?

What about the installs.ini file?

---

### Post by Skaperen on 2020-03-12
i don't have either file.

---

### Post by ipv on 2020-03-14
do this :

```
about:profiles
```

it will give you this :

[ATTACH=CONFIG]285212[/ATTACH]

follow instructions from here : [https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-remove-switch-firefox-profiles)

---

