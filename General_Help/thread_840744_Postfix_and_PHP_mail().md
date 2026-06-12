---
title: "Postfix and PHP mail()"
date: 2008-06-25
forum: General Help
---

### Post by rem on 2008-06-25
Hello,

I've been struggling for the past days to get Postfix send my PHP emails. I'm running a development server and can't properly test my PHP applications. Since on Gutsy everything worked fine, I did had some troubles before ([http://ubuntuforums.org/showthread.php?t=196039](http://ubuntuforums.org/showthread.php?t=196039)) but it seems the old fixes are not good anymore on Hardy.

Can anyone please share a Postfix (or other MTA) success story?

Thanks a lot!

P.S. I use XAMPP installation because of the PHP bundled GD library

---

### Post by rem on 2008-06-25
Can't believe how easily things get solved AFTER asking for help! I actually replaced Postfix with Sendmail and it worked out of the box. I always avoided to use Sendmail because it's hard configuration options but this time it was just installing it and restarting the Apache.

I really hope this will work for others with this problem as easy as it did for me!

---

