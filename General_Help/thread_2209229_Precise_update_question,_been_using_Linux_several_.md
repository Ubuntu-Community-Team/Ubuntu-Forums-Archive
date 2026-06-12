---
title: "Precise update question, been using Linux several years!"
date: 2014-03-04
forum: General Help
---

### Post by MikRose on 2014-03-04
I was getting messages that my updates "Failed to fetch from CD Rom...".  I've (finally) researched and have now unchecked the CD-Rom boxes in Update Manager's "Ubuntu Software", and also in the "Other Software" I found no other CD Rom terms used in any of the lines.  This has cleaned up a lot of what I had in the initial messages of "Failures", but still have this remaining and wondered if it is a problem:

W:Failed to fetch [http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages](http://dl.google.com/linux/deb/dists/testing/non-free/binary-i386/Packages)  404  Not Found [IP: 74.125.224.37 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Thanks

---

### Post by papibe on 2014-03-04
Hi MikRose.

I believe you installed either Chrome or the HangOut/GoogleTalk Firefox plugin. That adds a Google repository to your sources.

The error is reporting that the Google repository in not available. This is not a major error, and it only stops you from updating software from Google (while the repository is not available). For the regular software you can continue to both install new software, and upgrade normally.

Try updating your sources again in an hour or so.

Hopes it help. Let us know how it goes.
Regards.

---

### Post by monkeybrain20122 on 2014-03-04
So goolge's server is down. The update manager would not go through if even one source is temporarily not available. I would install synaptic and use to update manually and forget about the update manager. In synpatic you can also easily disable the problematic repository (go to Settings > Repositories > Other Software and uncheck the box for the offending repository)

 You can also do this by going into /etc/apt/sources.list.d, find the .list file for the repository, open it with gksudo gedit and then comment out all the lines (by placing a # in front) but it is easier to do it with synaptic.

---

### Post by MikRose on 2014-03-09
Thanks, I got er done!  I used to use Synaptic manager all the time, but Update Mgr popped up a while back and never have liked it real well.  I will do as you say, which I did, and it worked.  Thanks

---

### Post by MikRose on 2014-03-09
Thanks for the reply.  I found the Google line using Synaptic and eliminated it, so far so good.  Great to have help, love it.

---

