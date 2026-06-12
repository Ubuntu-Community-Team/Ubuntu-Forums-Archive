---
title: "The generated cache was invalid? How do I fix this?"
date: 2016-05-30
forum: General Help
---

### Post by argonvegell on 2016-05-30
I'm running Xubuntu 14.04, I'm planning on upgrading to 16.04 next year.

Anyway, I've installed ubudao-style 1.4.5 Icon theme from the Noobslab PPA, but I'm getting a warning that ubudao-style 1.4.5 has no cache file, so I went to the Terminal  as instructed and here's the results:

gtk-update-icon-cache /home/~/.icons/ubudao-style/
gtk-update-icon-cache: The generated cache was invalid.

After much digging around, I learned that icon-theme.cache is used to avoid a lot of system call and disk seek  overhead when the application starts and since the format of the cache  files allows them to be memory mapped shared between multiple  applications, the overall memory consumption is reduced as well.

---

### Post by pissedoffdude on 2016-05-30
Hi,

Per [https://github.com/numixproject/numix-icon-theme-circle/issues/639]("https://github.com/numixproject/numix-icon-theme-circle/issues/639") this is more of a WARNING than an actual error indicating that the icon names have spaces.  Unless you see a functional impact, it's safe to ignore it.  Otherwise, it would be best to file a bug report for that icon theme

---

### Post by argonvegell on 2016-05-30
Thanks for the reply, while it doesn't really affect my system, it's safe to ignore it, but I do find it annoying to see a warning label.

is there any way to flush out the filenames with spaces?

---

### Post by pissedoffdude on 2016-05-30
You can use [http://unix.stackexchange.com/questions/9496/looping-through-files-with-spaces-in-the-names](http://unix.stackexchange.com/questions/9496/looping-through-files-with-spaces-in-the-names) with the 'find' command to locate them.

I'm not familiar with theme development, but there may be a few references to those files, so proceed with caution.  You may be able to do a grep -nri "fire fox.png" . within the entire theme directory to find them though

---

### Post by argonvegell on 2016-05-31
I've successfully removed the files with filenames that has spaces on it, however, when I tried the gtk-update-icon-cache command, it still have the generated cache was invalid result.

Thanks for the help, I'll be using the icon theme with the cache file then, since it's not really affecting my system, thanks again.

---

