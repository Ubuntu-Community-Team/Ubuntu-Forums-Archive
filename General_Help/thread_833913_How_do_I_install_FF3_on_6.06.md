---
title: "How do I install FF3 on 6.06?"
date: 2008-06-19
forum: General Help
---

### Post by cjax1 on 2008-06-19
Hi. I am wanting to try FF3 (downloaded it from the mozilla site on the 18th) on 6.06 but I get a message that I need GTK+2.10 or newer. My system has GTK2.8. I tried to install GTK2.12.10. Naturally I find out that I need other stuff along with GTK like ATK and pango and cairo. After running the command

```
./configure --prefix=/opt/gtk
```

I get this towards the end


[B]checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.13.5    atk >= 1.9.0    pango >= 1.17.3    cairo >= 1.2.0) were not met:
Requested 'glib-2.0 >= 2.13.5' but version of GLib is 2.10.3
No package 'atk' found
No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/B]


So I guess this is dependency hell once again? Some kind of hell I never got out of before. So I guess this means I need ATK and pango and cairo. And I bet that even if I did somehow manage to get all those installed there would be more. Is this even worth it and is it possible? To me it's not the end of the world if I can't use FF3 in 6.06. I'm happy with FF 2.0.0.14. But am I doing something wrong? Is there an easier way or is FF3 just not compatible with 6.06? I tried opening FF as root and checking for updates but it said there are no updates available.

I'm not going back to 8.04. I think I'll wait till another release. But can I get FF3 in 6.06?

Thanks

---

### Post by p_quarles on 2008-06-19
Yes, if you're willing to put up with dependency hell, and possibly breaking your system :)

More seriously, I wouldn't recommend it. You're talking about a substantial number of new libraries, and many potential headaches down the road that may well negate the whole point of running a long term support release. If you're okay with Ff 2.x, stay with that.

---

### Post by cjax1 on 2008-06-19
ok thanks. I was worried about that breaking something else. Funny thing is I copied the FF3 download to my older laptop running Puppy 3.01. Extracted FF and simply started FF3 and it started right up. Just come to find out Puppy 3.01 has GTK 2.10 and pango. Go figure. Would be nice to have a way to update these things in older/current Ubuntu releases.

I'm not even going to try it.

Thanks for the reply.

---

