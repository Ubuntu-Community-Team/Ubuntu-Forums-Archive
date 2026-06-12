---
title: "Ubuntu 6.06 - HP F380 AIO"
date: 2006-12-07
forum: General Help
---

### Post by shookone on 2006-12-07
I had previously installed this darn printer successfully. Now for some reason when i goto print it starts to feed the paper then it doesn't print anything just gets stuck on printing the first line.


Power button starts to blink. 

My /var/log/cups/error_log shows:

```

E [07/Dec/2006:21:43:43 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [07/Dec/2006:21:45:44 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [07/Dec/2006:21:45:53 -0500] cupsdAuthorize: Local authentication certificate not found!
E [07/Dec/2006:21:45:53 -0500] cupsdAuthorize: Local authentication certificate not found!
E [07/Dec/2006:21:45:58 -0500] cupsdAuthorize: Local authentication certificate not found!
E [07/Dec/2006:21:45:58 -0500] cupsdAuthorize: Local authentication certificate not found!
E [07/Dec/2006:21:45:58 -0500] cupsdAuthorize: Local authentication certificate not found!
E [07/Dec/2006:21:46:02 -0500] cupsdAuthorize: Local authentication certificate not found!
E [07/Dec/2006:21:46:02 -0500] CUPS-Delete-Printer: Unauthorized
E [07/Dec/2006:21:46:55 -0500] CUPS-Add-Modify-Printer: Unauthorized


```

Please assist.

This thing works in windows.... but in ubuntu doesn't do anything. It used to work!!! ahhh!!

---

