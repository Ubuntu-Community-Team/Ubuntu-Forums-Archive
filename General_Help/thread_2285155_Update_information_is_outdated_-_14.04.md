---
title: "Update information is outdated - 14.04"
date: 2015-07-03
forum: General Help
---

### Post by pancho5 on 2015-07-03
Hello!

As per attachment, I am getting the following error message as you can see the annoying red triangle on the top of the screen.  I executed the sudo apt-get update command, and the following error message displays.

What do I have to do to resolve the problem?  I've used Ubuntu 14.04 since April of this year, but not technically astute enough to solve this problem.

Any help/advice would be greatly appreciated from any Senior Ubuntu/Linux techie! :neutral:

TIA!

---

### Post by howefield on 2015-07-03
If you go load up Software & Updates > Authentication tab, do you see a key for Spotify, similar to the attached image.

---

### Post by pancho5 on 2015-07-03
> **howefield said:**
> If you go load up Software & Updates > Authentication tab, do you see a key for Spotify, similar to the attached image.


Yes I do...see attachment pic.

---

### Post by howefield on 2015-07-03
Ok, try this terminal command

```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys D2C19886
```

then try to update, if it works then you can remove the old redundant non working key.

---

### Post by pancho5 on 2015-07-03
> **howefield said:**
> Ok, try this terminal command

```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys D2C19886
```

then try to update, if it works then you can remove the old redundant non working key.

Okay I will, but explain something to me...what am I doing here?  If it does work, how do I remove the old key?

---

### Post by howefield on 2015-07-03
You are replacing an old expired and therefore redundant authentication key with the current working one.

To remove the old one, simply highlight the key in Software & Updates > Authentication tab and press the remove button, you will be prompted for your password, type it and press enter.

You needn't take my word for it, all the instructions are on the spotify website, and you will also find posts in the spotify forum regarding this very issue.

---

### Post by pancho5 on 2015-07-04
> **howefield said:**
> You are replacing an old expired and therefore redundant authentication key with the current working one.

To remove the old one, simply highlight the key in Software & Updates > Authentication tab and press the remove button, you will be prompted for your password, type it and press enter.

You needn't take my word for it, all the instructions are on the spotify website, and you will also find posts in the spotify forum regarding this very issue.

Thank you sir!

---

