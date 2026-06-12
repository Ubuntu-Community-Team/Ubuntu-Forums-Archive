---
title: "Ubuntu ISO images"
date: 2008-03-13
forum: General Help
---

### Post by wjhildreth on 2008-03-13
I was just wondering. With the upcoming release of 8.04 I know that an ISO will be available. And through the course of time there will be updates coming along. My question is, is the ISO updated to reflect those changes, or is it the same ISO that was originally put out?

Warm Regards,

Joe Hildreth
Waverly, TN

---

### Post by ugm6hr on 2008-03-13
The iso remains unchanged.

However, for LTS releases (like 8.04), there will likely be an updated iso at some point during the support cycle.  It took about 18 months for 6.06LTSv2 though...

---

### Post by wjhildreth on 2008-03-13
I was just wondering. I can see a new install taking some time with updates and what not without an updated ISO. I guess it was just one of those questions that pop in your head.

Thanks for such a quick reply.

Regards,

Joe

---

### Post by ugm6hr on 2008-03-14
If you have already installed and downloaded updates, you can back the updates up from */var/cache/apt/archives*

Just copy them back to the same location after a fresh re-install, and it should be quicker.

I have heard people use apt-on-cd to do this too, but I just tar all the files to my backup HD.  Obviously, you have to use sudo permissions to copy the files back.

Hope that helps with whatever reinstallation plans you have.

---

### Post by wjhildreth on 2008-03-14
That tid bit of info is very helpful. Thanks so much for your time and energy. I appreciate it.

Regards,

Joe

---

