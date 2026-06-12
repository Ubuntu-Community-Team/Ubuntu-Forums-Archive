---
title: "Wget--change downloaded file name, pipe?"
date: 2008-06-19
forum: General Help
---

### Post by swordsmith on 2008-06-19
Hi all,
I'm writing a program in python that uses wget to download images to a directory and change the file name to conform to a certain pattern. I've read through the wget manual but cannot find a way to change the name of the downloaded file.
Also, is there a way to pipe the output of wget to do that? That would be extremely convenient.

Thanks

---

### Post by sdennie on 2008-06-19
You should be able to do this with -O.  For instance:

```

wget http://some_url/foo.html -O bar.html

```

---

### Post by Cupster on 2009-04-27
thanks a lot for this info!
just what I needed

---

### Post by nikhilbhardwaj on 2011-05-16
thanks for this info,
i was looking for the exact same thing.
+1

---

### Post by undyingvisage58 on 2012-11-09
> **sdennie said:**
> You should be able to do this with -O.  For instance:

```

wget http://some_url/foo.html -O bar.html

```

hell yeah!! this is what i needed too! however it didnt work for me in the beginning. kept saying "-O <name.what.ever> not recognized"

so instead i put the -O command, with my desired file name, between the download site and wget. and it worked just fine!

---

### Post by llamabr on 2012-11-09
Please don't dig up old threads.  This was originally posted more than one year ago.

---

