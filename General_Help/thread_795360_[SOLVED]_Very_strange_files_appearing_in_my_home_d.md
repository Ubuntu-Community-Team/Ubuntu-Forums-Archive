---
title: "[SOLVED] Very strange files appearing in my home dir"
date: 2008-05-15
forum: General Help
---

### Post by schallstrom on 2008-05-15
Yesterday, suddenly these strange files somewhat looking like a URL query string appeared in my home dir and I have absolutely no idea where they come from. I'm a bit concerned if the could be left there by some kind of malware? Could anyone give me a hint what to do to investigate it? I searched the forums and google without useful results.

```

mo@molniya:~$ ls -l
total 1260688
-rw-r--r-- 1 mo mo       429 2008-05-14 22:53 ads-format=468x30_aff_img&client=ca-pandemia@mclink.net&channel=feed&output=png&cuid=1c6.JOj7kT.08574252.108x81_map.shtml
-rw-r--r-- 1 mo mo       433 2008-05-14 22:53 ads-format=468x30_aff_img&client=ca-pandemia@mclink.net&channel=feed&output=png&cuid=1c6.JOj7kT.08574252.226x170_map.shtml
-rw-r--r-- 1 mo mo       429 2008-05-14 21:46 ads-format=468x30_aff_img&client=ca-pandemia@mclink.net&channel=feed&output=png&cuid=1c6.JOj7kT.32185953.108x81_map.shtml
-rw-r--r-- 1 mo mo       433 2008-05-14 21:46 ads-format=468x30_aff_img&client=ca-pandemia@mclink.net&channel=feed&output=png&cuid=1c6.JOj7kT.32185953.226x170_map.shtml
-rw-r--r-- 1 mo mo       429 2008-05-14 21:16 ads-format=468x30_aff_img&client=ca-pandemia@mclink.net&channel=feed&output=png&cuid=1c6.JOj7kT.69143681.108x81_map.shtml
-rw-r--r-- 1 mo mo       433 2008-05-14 21:16 ads-format=468x30_aff_img&client=ca-pandemia@mclink.net&channel=feed&output=png&cuid=1c6.JOj7kT.69143681.226x170_map.shtml
-rw-r--r-- 1 mo mo       429 2008-05-14 22:47 ads-format=468x30_aff_img&client=ca-pandemia@mclink.net&channel=feed&output=png&cuid=1c6.JOj7kT.88379342.108x81_map.shtml
-rw-r--r-- 1 mo mo       433 2008-05-14 22:47 ads-format=468x30_aff_img&client=ca-pandemia@mclink.net&channel=feed&output=png&cuid=1c6.JOj7kT.88379342.226x170_map.shtml

```

---

### Post by Mr A Mouse on 2008-05-15
> **schallstrom said:**
> Yesterday, suddenly these strange files somewhat looking like a URL query string appeared in my home dir and I have absolutely no idea where they come from. I'm a bit concerned if the could be left there by some kind of malware? Could anyone give me a hint what to do to investigate it? I searched the forums and google without useful results.


This looks like some form malformed internet content: it's from mclink.net. If MC-Link.net is your internet service provider, then at least we know where they came from.

1: What kind of browser are you using?
2: If you open one of the files in a text editor, does it look like HTML code? If so, what does it say?

---

### Post by schallstrom on 2008-05-15
Sorry, I should have been giving more info in the first place.

mclink.net seems to be a provider from a Spanish speaking country or something like this. I never heard of them before and certainly never consciously visited their website before I got aware of the files.

I'm using Firefox 3.0b5 in Hardy.

The files contents look sth. like this:
```

mo@molniya:~$ cat ads-format\=468x30_aff_img\&client\=ca-pandemia@mclink.net\&channel\=feed\&output\=png\&cuid\=1c6.JOj7kT.08574252.108x81_map.shtml 
<map id="ads-format=468x30_aff_img&client=ca-pandemia@mclink.net&channel=feed&output=png&cuid=1c6.JOj7kT.08574252.108x81" name="ads-format=468x30_aff_img&client=ca-pandemia@mclink.net&channel=feed&output=png&cuid=1c6.JOj7kT.08574252.108x81">
  <area href="ads-format=468x30_aff_img&client=ca-pandemia@mclink.net&channel=feed&output=png&cuid=1c6.JOj7kT.08574252.108x81_map.shtml" shape="rect" coords="0,0,107,80" alt="" />
</map>

```To me this doesn't look harmful, but maybe I just lack the skills to see it...

Oh, and isn't your conclusion that it is **from** mclink.net over-hasty? [email]ca-pandemia@mclink.net[/email] could just be an email address...

---

### Post by Mr A Mouse on 2008-05-15
Aha! It's an image-map file! 

This used to be how clickable image maps were set up. Most websites now include the map coordinates in the HTML file--this is the older way to do things.

ETA: It's no big deal--just an example of sloppy programming on their part.

---

### Post by elamericano on 2008-05-15
Are you not saving web pages?

Otherwise why would it get saved in the home directory without any user interaction? Whether it's the browser doing it or some other app, I'd still worry.

---

### Post by chrisccoulson on 2008-05-15
> **elamericano said:**
> Are you not saving web pages?

Otherwise why would it get saved in the home directory without any user interaction? Whether it's the browser doing it or some other app, I'd still worry.

This is the very reason I sandbox Firefox very tightly with Apparmor!

---

### Post by Mr A Mouse on 2008-05-15
> **elamericano said:**
> Otherwise why would it get saved in the home directory without any user interaction?

This is how browsers handled older web pages with a separate map file for their imagemaps.

---

### Post by schallstrom on 2008-05-15
> **Mr A Mouse said:**
> This is how browsers handled older web pages with a separate map file for their imagemaps.

I really don't think that Firefox is supposed to write any data on my hard disk besides the cached sites and cookies, and certainly it should not write into my ~/ dir without requesting me to do so and absolutely certainly not from a web page I never actively surfed to because I don't even speak the language of the page!

So I'm still concerned and would be very very thankful for any insightful hints.

---

### Post by Mr A Mouse on 2008-05-15
> **schallstrom said:**
> I really don't think that Firefox is supposed to write any data on my hard disk besides the cached sites and cookies, and certainly it should not write into my ~/ dir without requesting me to do so and absolutely certainly not from a web page I never actively surfed to because I don't even speak the language of the page!

So I'm still concerned and would be very very thankful for any insightful hints.

I can certainly understand the concern ... but I'm not sure I have much in the way of insight, I fear.

It is possible that mclink purchased advertising space on a website that you did visit: if they did their advertising in the form of an iframe or a page in a frameset, this would explain where the data came from.

As for Firefox, it is possible that Firefox inherits your permissions, and thus can write where you can write. I fear I know little about browser programs, but this is definitely something I would mention to the folks at Mozilla.

One thing that may help, if you've not already done so, is to install the Adblock Plus plugin for Firefox. I have found it to be quite effective in blocking information I do not want.

---

### Post by schallstrom on 2008-05-16
> **Mr A Mouse said:**
> 
One thing that may help, if you've not already done so, is to install the Adblock Plus plugin for Firefox. I have found it to be quite effective in blocking information I do not want.

Yes, I'm already using Adblock.

---

### Post by schallstrom on 2008-06-15
Through long-term observation I found out, that miro is to blame. The files only appear after using miro and I found some relevant strings from the file names in ~/.miro/sqlitedb.

---

