---
title: "Two Firefox profiles open at the same time? [Resolved]"
date: 2007-04-14
forum: General Help
---

### Post by x1a4 on 2007-04-14
Hi,

Is it possible to have two (or more) instances of Firefox open with two profiles at the same time? For example, two instances of one profile open in one workspace and another instance of Firefox with a different profile open in another workspace.  

Thank you.

---

### Post by aysiu on 2007-04-14
Maybe you could get something close by creating a separate user account and then using *gdmflexiserver --xnest* to open a new window running another Firefox session within that window?

---

### Post by x1a4 on 2007-04-14
> **aysiu said:**
> Maybe you could get something close by creating a separate user account and then using *gdmflexiserver --xnest* to open a new window running another Firefox session within that window?

Since there are several people using the computer, and most of us have multiple user accounts created, we use *gdmflexiserver* quite often.  

The problem is that more often than not, it's just me and my girlfriend, and the way we use the computer is that I use it, then leave it, she comes by wants to continue whatever she was doing earlier, then leaves it, I come again and want to continue whatever I was doing.  

Typically, we're logged into one account and switch between workspaces, it's much easier, except when browsing the Web when we have to close Firefox then reopen it.  I have the 'Save Session' plug-in installed so it's not that big of a problem, but I was hoping things could get a little bit easier.  

Oh well.  I'll send a wish list request to Mozilla--maybe the next version will allow for multiple profiles to be open at the same time.  

Thank you for your timely reply.

---

### Post by aysiu on 2007-04-14
But ```
gdmflexiserver --xnest
``` allows you to have sessions at once with one session being inside the other session in a new window. It's different from regular ```
gdmflexiserver
```

---

### Post by Sencer on 2007-04-15
> **x1a4 said:**
> Hi,

Is it possible to have two (or more) instances of Firefox open with two profiles at the same time? For example, two instances of one profile open in one workspace and another instance of Firefox with a different profile open in another workspace.  

Thank you.

Yes, to most of the questions. Use the "-no-remote" command-line switch.

firefox -no-remote -ProfileManager

Will also allow you to select a Profile for the new instance (you can't run seperate instances of the same profile at the same time).

Or if you want shortcuts, you can run it with:

firefox -no-remote -P nameofprofile

(nameofProfile is what is shown in the Profile-Manager. You can also check it in ~/.mozilla/firefox/profiles.ini)

---

### Post by Sencer on 2007-04-15
Duplicating a profile is relatively easy. Simply copy the directory to a new one, and run a search & replace through the new files for th eold directory name.

 ```

cd ~/.mozilla/firefox/
cp -dPR oldprofile/* newprofile/
find newprofile/ -type f -print0 | xargs -0 sed -ir "s|oldprofile|newprofile|g"
 
```

Now, finally open profiles.ini and add another block there for the new profile:

```


[Profile4]
Name=someNameyouLIke
IsRelative=1
Path=newprofile

```


I've made myself a shellscript to copy the profile to a new profile and start that. If the new profile already exists, delete it first. That way the new, cuplicated profile is always up to date (but changes to the duplicate are obviously lost, when I delete/overwrite it).

---

### Post by aysiu on 2007-04-15
> **Sencer said:**
> Yes, to most of the questions. Use the "-no-remote" command-line switch.

firefox -no-remote -ProfileManager

Will also allow you to select a Profile for the new instance (you can't run seperate instances of the same profile at the same time). That's amazing! I never knew you could do that. Thanks for sharing.

---

### Post by Sencer on 2007-04-15
Hi aysiu, 

given that I've seen so many very hepful and informative postings from you, I am glad I was able to contribute a little bit as well. :)

---

### Post by aysiu on 2007-04-15
Thanks... and thanks.

I like collecting little tidbits like this. You made my day.

---

### Post by x1a4 on 2007-04-15
> **Sencer said:**
> Yes, to most of the questions. Use the "-no-remote" command-line switch.

firefox -no-remote -ProfileManager

*<snip>*

Thank you.

---

### Post by x1a4 on 2007-04-15
> **Sencer said:**
> Duplicating a profile is relatively easy. Simply copy the directory to a new one, and run a search & replace through the new files for th eold directory name.

*<snip>*

And Thank You.

---

