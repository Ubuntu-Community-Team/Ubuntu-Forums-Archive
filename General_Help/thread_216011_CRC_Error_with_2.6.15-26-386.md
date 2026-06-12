---
title: "CRC Error with 2.6.15-26-386"
date: 2006-07-14
forum: General Help
---

### Post by Freddie on 2006-07-14
Today I updated my kernel version from 2.6.15-25-386 to (using apt-get dist-upgrade) 2.6.15-26-386), along with the modules that came with it.

However, when I rebooted I found that there was an error uncompressing the kernel; something along the lines of a CRC error, which caused a system halt. So, I rebooted, pressing ESC at the grub menu and then booted back into my 2.6.15-25-386 kernel with no trouble at all.

After attempting to fix the problem using Synaptic (and failing, by re-installing the kernel) I decided to edit my grub config file and commented out the top two entries, which seems to have worked fine.

However, I am still unsure about what to do to fix the problem--does anyone have any ideas?

I have taken a quick look at the sticky, but am unsure if it is relevant to me. I have not compiled any third party modules myself and so am not sure what to do and yes, I do have the kernel-386 package installed on my computer.

Regards, Freddie.

---

### Post by Polygon on 2006-07-15
not an expert here, but maybe one the files that got downloaded by the installer got corrupt in some way? maybe just try going into synaptic and redownload/install the new kernel and see if that works.

---

### Post by Freddie on 2006-07-15
That could well be the case, however I thought that apt was smart enough to verify downloaded information before installing it to prevent this kind of problem.

I have gone and re-installed basically everything under the sun with no luck at all.
Never mind I am sure that someone will come up with a solution sooner or later.

---

### Post by givré on 2006-07-15
He is smart enough indeed.
Try to boot in recovery mode and see where it hangs.

---

### Post by Freddie on 2006-07-15
I rebooted it in recovery mode and got exactly the same result as I did when I tried it in normal mode:
```

crc error

-- System Halt

```

---

### Post by givré on 2006-07-15
Ok, it seems important.
Fill a bug [https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug)

---

### Post by Freddie on 2006-07-15
Done: [https://launchpad.net/distros/ubuntu/+bug/53078](https://launchpad.net/distros/ubuntu/+bug/53078)

---

