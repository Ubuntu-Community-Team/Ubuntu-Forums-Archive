---
title: "Cannot read DVDs"
date: 2007-04-21
forum: General Help
---

### Post by lijamez on 2007-04-21
I have two LG DVD drives in Ubuntu 7.04, I get this error when putting a DVD disc in:
Cannot mount volume.
Invalid mount option when attempting to mount the volume 'UDF Volume'.

What's the problem? :(

---

### Post by Wight_Rhino on 2007-04-22
I too, am having this problem in Feisty. Any ideas?

I had no problem until the upgrade, and I'm probably going back to Edgy for now.:(

---

### Post by fede on 2007-04-24
Same problem here!

---

### Post by loathsome on 2007-05-26
BUMP!

Same problem here

---

### Post by mdurham on 2007-05-26
I think we just have wait for the next kernel release. I upgraded to Gutsy and installed kernel 2.6.22 and now my LG CD/DVD works fine. It didn't work at all before using the new kernel.
Cheers, Mike

---

### Post by loathsome on 2007-05-26
Is it possible to install the new kernel in Feisty?

---

### Post by mdurham on 2007-05-26
> **loathsome said:**
> Is it possible to install the new kernel in Feisty?

I don't know, maybe ask in a new thread and hope an expert sees it.

---

### Post by DeathStar on 2007-05-27
Hi Everyone,

I was having this issue for ages and it was driving me mad. CD would mount with no problems, but DVD's just wouldn't.

Like you, I have tried most solutions out there with no joy, however, I manged to get it working this morning.

The issue for me was that the libdvdcss2 didn't want to work properly. After readng LOTS of forum posts on this, a lot of people were suggesting getting libdvdcss2 from the MEDIBUNTU repository...

See here:
[http://ubuntuforums.org/showpost.php?p=2727375&postcount=3]("http://ubuntuforums.org/showpost.php?p=2727375&postcount=3")

Then, once you've added those repositories, try installing libdvdcss2 again. This time it should get it from the new repository:

```

sudo apt-get update
sudo apt-get install libdvdcss2

```

If that doesn't work (which for me it didn't at first) then check your Update Manager in Gnome. I had 3 "new" updates in there and one of them was an updated libdvdcss2. I installed those update and then it worked!

This worked for me. If it works for you, can you please post a link to this forum in an places where people are having the same issues. If it doesn't work for you, my advice is to keep reading. These is a wealth of infomration in these forums, it's just a bit difficult to find some times.

You will get it sorted eventually!

Hope this helps!
DS.

---

### Post by loathsome on 2007-05-27
> **DeathStar said:**
> Hi Everyone,

I was having this issue for ages and it was driving me mad. CD would mount with no problems, but DVD's just wouldn't.

Like you, I have tried most solutions out there with no joy, however, I manged to get it working this morning.

The issue for me was that the libdvdcss2 didn't want to work properly. After readng LOTS of forum posts on this, a lot of people were suggesting getting libdvdcss2 from the MEDIBUNTU repository...

See here:
[http://ubuntuforums.org/showpost.php?p=2727375&postcount=3]("http://ubuntuforums.org/showpost.php?p=2727375&postcount=3")

Then, once you've added those repositories, try installing libdvdcss2 again. This time it should get it from the new repository:

```

sudo apt-get update
sudo apt-get install libdvdcss2

```

If that doesn't work (which for me it didn't at first) then check your Update Manager in Gnome. I had 3 "new" updates in there and one of them was an updated libdvdcss2. I installed those update and then it worked!

This worked for me. If it works for you, can you please post a link to this forum in an places where people are having the same issues. If it doesn't work for you, my advice is to keep reading. These is a wealth of infomration in these forums, it's just a bit difficult to find some times.

You will get it sorted eventually!

Hope this helps!
DS.
Thanks for your nice post :)

Though, this has only happened to me with one DVD, all the others I've tried have worked. So, if this happens again, I'll try your solution.

Have a nice day! :KS

---

