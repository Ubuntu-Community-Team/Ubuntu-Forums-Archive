---
title: "Disk space disappears much faster than I put data on it."
date: 2017-12-06
forum: General Help
---

### Post by Roland_Msl on 2017-12-06
I have Ubuntu 16.04.
My SSD is romatted with 0,5 GB boot, 8 GB Swap, the rest is EXT4.

As I started summer 2916, I had about 50 GB free. Thiught this will be enoug for some years.

Now System Monitor shows:

/dev/sda2
ext4
Total 463,6 GB
Available 4,4 GB
Used 435,6 GB

But 435,6 GB used and 4,4 GB available is 440 GB.
What is with the difference between 440 GB and Total 463,6 GB?

---

### Post by Bashing-om on 2017-12-06
Roland_Msl; Hello -

Let's see where the space is used and then see what can be done to free up space.

Post back - Between code tags - the outputs of terminal commands:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

df -h
df -i
cd /
sudo du -sx * | sort -n
cd

```
As a 1st step 
[INDENT][INDENT]see where we go from here
[/INDENT][/INDENT]

---

### Post by Impavidus on 2017-12-07
> **Roland_Msl said:**
> 
But 435,6 GB used and 4,4 GB available is 440 GB.
What is with the difference between 440 GB and Total 463,6 GB?

The difference is that 5% of your disk space is reserved for emergency use. Only root can write to that, so it's not available for the ordinary user. You can tune that percentage if you want, but it's not going to buy you much. If you filled 95% of the partition in a year and a half, you will fill the remaining 5% in a month. So it's time to get more storage space or a do good clean-up.

Bashing-om gave you some commands to find out where your disk space went. [This howto](https://ubuntuforums.org/showthread.php?t=1122670) may be helpful too. It's a bit older, but most of it still applies.

---

### Post by Roland_Msl on 2017-12-08
I did not fill this in one year, I did this since 1987. When I copied all to the new notebook, I had about 50 GB free. Since I started this thread, 0,8 GB less and I have no idea why, because I only downloaded 0,1 GB PDF. The other 0,7 GB are mysterious.

---

### Post by Yellow Pasque on 2017-12-08
> **Roland_Msl said:**
> I did not fill this in one year, I did this since 1987. When I copied all to the new notebook, I had about 50 GB free. Since I started this thread, 0,8 GB less and I have no idea why, because I only downloaded 0,1 GB PDF. The other 0,7 GB are mysterious.

^That tells us nothing. You would have a much better chance of solving your problem if you followed directions/suggestions...

---

