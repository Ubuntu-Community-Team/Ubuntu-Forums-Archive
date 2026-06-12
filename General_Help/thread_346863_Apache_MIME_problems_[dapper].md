---
title: "Apache MIME problems [dapper]"
date: 2007-01-26
forum: General Help
---

### Post by ruanza on 2007-01-26
Hi everybody,

I am having endless problems trying to get Apache's Mime types working correctly on Dapper Drake.

I want to add the mime type audio/amr amr and did so in /etc/apache2/apache2.conf like this:

AddType audio/amr amr

This had no effect. I then tried with .htaccess and setting AllowOverride on for that directory. This also had no effect.
I then tried adding the mime type to /etc/mime.types. No effect.
Also as a last resort tried to add the mime magic module. Also no effect.

After each of these steps, I restarted Apache and cleared my browser cache.

If I point my browser to the AMR file on my site, it still loads up inside the browser and the browser attempts to display it as opposed to asking me to download it.

Also, this causes mobile devices not to recognise this file as audio.

Any ideas anybody? Any help will be appreciated.

Regards
Ruan

---

### Post by omghax on 2007-01-26
Seems like a noob question but, could it be your browser?

On my site, I use Apache and I have custom file extensions such as .TL -- *I use pngfix for IE users, but I have a image randomization script for PNG's and it gets confused and never stops loading.*

I just recently reformatted my Webserver to Dapper again, and I reinstalled Apache from scratch. Didn't seem to have any problems with the MIME stuff, I can't get onto it right now but I believe I tried everything you did but eventually one of those worked.


I'll try it out later, once SSH kicks back in.

**EDIT**: Is it because you forgot a .?
e.g.: AddType audio/amr .amr

---

### Post by ruanza on 2007-01-26
Hi thanks for the quick reply.

Hmm no the . in front of the extension also does not make a difference.

And I have tried four different browsers. Both on mobile phone and XP.

In IE I get an 'unknown file type' dialog with a save button. It should say there audio/amr instead of 'unknown file type' I think if the mime types are working correctly. In Firefox it loads the contents of the file. Also the same thing on Opera and the built-in web browser on my 6680.

R

---

### Post by omghax on 2007-01-26
Well, I'm not sure what an AMR file is -- where can I get one so I can try this out?

---

### Post by ruanza on 2007-01-26
I can e-mail you one if you want, it is a mobile ringtone format and the one I am thinking of is about 80kb.

R

---

### Post by omghax on 2007-01-26
Oh! I forgot about those! I actually have done this in the past, and was thinking about doing it sooner or later.

I think I remembered doing the AMR section all caps though, don't know if that'll help. I'll try setting it up on my Webserver later today, now I gotta find some good ringtones.

P.S.> audio/AMR <-- that part

---

### Post by ruanza on 2007-01-26
I really don't think Mime types are case sensitive, anyways will try it quickly.

Nope. Does not make a difference.

There is something else - I swear it is ubuntu related cause I never struggled like this on freebsd. But I absolutely looooooove ubuntu, I can't believe that this cannot work!

R

---

