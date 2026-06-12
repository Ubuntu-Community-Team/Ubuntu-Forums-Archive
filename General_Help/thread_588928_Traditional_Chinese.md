---
title: "Traditional Chinese"
date: 2007-10-23
forum: General Help
---

### Post by ep2011 on 2007-10-23
I have simplified chinese working perfectly with Scim and Ubuntu Edgy, and I have traditional support installed, but for some reason whenever I go to traditional, it still types in simplified. Do I need to install traditional fonts? 
If so, how do I go about this? 
Thanks :)

---

### Post by chunchengch on 2007-10-23
setting in Language-Support window is just like the snapshot attached

[ATTACH]47522[/ATTACH]

---

### Post by ep2011 on 2007-10-23
chunchengch, I don't want everything in chinese, I just want to be able to type in traditional. The chinese checkbox is checked

---

### Post by chunchengch on 2007-10-23
ok! try this

[ATTACH]47523[/ATTACH]

---

### Post by ep2011 on 2007-10-23
Okay i did that but which one do I pick to use?

Theres Chewing, Quick, CangJie 3, Easy Big, Cantonese Pinyin, CNS11643, ZhuYin, Stroke 5, Wu, Simplex, Canton HK, Array30, CangJie 5, ZhuYin Big, Dayi3, CangJie and Jyutping.

Which one is pinyin? I tried Chewing and its really wierd

---

### Post by jenhsun on 2007-10-23
ep2011,
Fireup your scim gui setup and look into your Global setup (both frontend and IMEngine session).
Check or uncheck the input method you want. And use hotkey to trigger your input method on or off. 
You can play around with the SCIM input. Define your hotkey (reload/reboot your new setup if possible). That would be fun.

In addition, in Ubuntu Gutsy 7.10 the SCIM has some problems.
[https://bugs.launchpad.net/ubuntu/+bug/153233](https://bugs.launchpad.net/ubuntu/+bug/153233)

If you stick on Feisty, that would be fine.

---

### Post by ep2011 on 2007-10-24
Now I can type in Traditoinal.. But its Cantonese. How do i type in traditional mandarin? On simplified I just type ni *space* hao *space*, but if I do that with any of the traditionals, it looks very different.

---

### Post by jenhsun on 2007-10-24
> **ep2011 said:**
> Now I can type in Traditoinal.. But its Cantonese. How do i type in traditional mandarin? On simplified I just type ni *space* hao *space*, but if I do that with any of the traditionals, it looks very different.

See my solution here
[http://ubuntuforums.org/showthread.php?t=589279&highlight=scim](http://ubuntuforums.org/showthread.php?t=589279&highlight=scim)

Ya, I miss clear water beach...>_<

---

### Post by jenhsun on 2007-10-28
About anything related on SCIM, Problem solved.

Please take a look at this bug report
[https://bugs.launchpad.net/ubuntu/+bug/34282](https://bugs.launchpad.net/ubuntu/+bug/34282)
or here
[http://ubuntuforums.org/showpost.php?p=3676651&postcount=6](http://ubuntuforums.org/showpost.php?p=3676651&postcount=6)
And the most important is the document in your
/usr/share/doc/scim/README.Debian.gz

---

