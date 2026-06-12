---
title: "About dd command"
date: 2014-02-08
forum: General Help
---

### Post by Stormlord on 2014-02-08
Hi.  I am studying "dd" and its options.  I see that the befault block size is 512 but it offers the option bs= for us to change it.  It's not quite clear what a change like that would offer.  Can you help please?  What is this actually doing?  Does it make a copy faster for example?  When do we need to change this value?

Thank you!

---

### Post by deadflowr on 2014-02-08
This might give a nice answer to what it means and such
[http://stackoverflow.com/questions/6161823/dd-how-to-calculate-optimal-blocksize](http://stackoverflow.com/questions/6161823/dd-how-to-calculate-optimal-blocksize)

---

### Post by Stormlord on 2014-02-08
> **deadflowr said:**
> This might give a nice answer to what it means and such
[http://stackoverflow.com/questions/6161823/dd-how-to-calculate-optimal-blocksize](http://stackoverflow.com/questions/6161823/dd-how-to-calculate-optimal-blocksize)

Yes, this was very helpful indeed, especially this statement here: "for better accurancy and data recovery set the blocksize to the native sector size of the input".

This means that using fdisk -l prior to a disk copy, will show what needs to be used.  :)

Thanks a lot.  :)

---

