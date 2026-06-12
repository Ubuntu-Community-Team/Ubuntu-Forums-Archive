---
title: "Kernel Compilation Error"
date: 2014-08-21
forum: General Help
---

### Post by richard82 on 2014-08-21
Im compiling the google play edition kernel for the htc one m8 varient. The kernel is 3.4.0-gb1b6fb1 for android 4.4.4. So here is the error:
>   CC      arch/arm/mach-msm/htc_acoustic_alsa.o
arch/arm/mach-msm/htc_acoustic_alsa.c: In function 'acoustic_ioctl':
arch/arm/mach-msm/htc_acoustic_alsa.c:257:43: warning: 'mid' may be used uninitialized in this function [-Wuninitialized]
error, forbidden warning: htc_acoustic_alsa.c:257
make[1]: *** [arch/arm/mach-msm/htc_acoustic_alsa.o] Error 1
make: *** [arch/arm/mach-msm] Error 2
 

and here is section in the file htc_acoustic_alsa.c that supposidly contains the error on line 257 which is if(copy_to_user((void *)arg, mid, strlen(mid))) {:

> 
case ACOUSTIC_GET_MID:
        if (the_ops->get_mid)
            mid = the_ops->get_mid();

        D("get mid: %s\n", mid);
        if(copy_to_user((void *)arg, mid, strlen(mid))) {
            E("acoustic_ioctl: copy to user failed\n");
            rc = -EINVAL;
        }
        break;  


Any ideas on how to correct this error? Im very new to c language and need help badly. Thank you.

---

