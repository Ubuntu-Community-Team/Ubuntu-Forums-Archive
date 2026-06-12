---
title: "Could NOT find TIFF (missing: TIFF_LIBRARY TIFF_INCLUDE_DIR)"
date: 2017-11-08
forum: General Help
---

### Post by ammouna2 on 2017-11-08
Hello,

I installed tiff library by sudo apt-get install however I get this error : Could NOT find TIFF (missing: TIFF_LIBRARY TIFF_INCLUDE_DIR).

Could someone explain to me what the problem ? and how to solve it ?

Thank you very much.

Best regards,

---

### Post by steeldriver on 2017-11-08
It's hard to say - since you're giving us absolutely no context

If we guess that you are trying to build some software from source that relies on libtiff, then probably what you need to do is install the development package **libtiff5-dev** and then re-run whatever build configuration steps are required to locate the headers

---

### Post by oldos2er on 2017-11-08
Thread moved to General Help.

---

