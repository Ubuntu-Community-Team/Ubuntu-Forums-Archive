---
title: "&quot;The disk contains an unclean file system&quot;"
date: 2014-06-16
forum: General Help
---

### Post by cdiaz3827 on 2014-06-16
Long story short, everytime I had my second internal hard drive (no OS, simply used it as a media drive to store music, videos, pics, etc) it would corrupt my installation on Windows (I ONLY had Windows installed, I don't and never have used Ubuntu on this comptuer) so I reformatted my main drive with Windows 8 and just kept my secondary drive unplugged. But now I really need the data on that, so to protect my current drive and data, I unplugged my main drive, plugged my media drive back in and booted into Ubuntu off my flash drive. I keep trying to mount my media drive to recover that data then reformat it, but I keep getting 
> Error mounting system-managed device /dev/sda1: Command-line `mount "/mnt/5CAA8184AA815B80"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

I've read around the forums and eventually realized its windows stupid fast boot causing the problem, and I have to boot back into Windows and turn fast boot off. Problem is this drive doesn't have Windows 8 on it, and if I plug my drive with Windows 8 back in I can never boot into Windows, it just corrupts the entire installation. How can I recover my data from Linux now? I've tried adding "remove_hiberfile" to the boot options but nothing happens. 

Any ideas? Thanks, I really appreciate it. This makes me fed up with Windows all over again and this media drive will definitely have Ubuntu on it when this is all over.

---

### Post by yancek on 2014-06-16
> or mount the volume
read-only with the 'ro' mount option. 			 		

If you want to copy data from the corrupted drive, the above should work as you have no need to write to it.
I don't really understand as in your first paragraph you state that " so I reformatted my main drive with Windows 8 and just kept my secondary drive unplugged" which I would take to mean you have windows 8 installed and working??  In the second paragraph you indicate the following:

> if I plug my drive with Windows 8 back in I can never boot into Windows, it just corrupts the entire installation

Does that mean if you have the corrupted drive attached when you boot windows 8 you have problems?  What happens?  Did you try attaching the bad drive after booting windows 8?  I don't see how even having a bad data partition on a secondary drive would do that.  More details might help.

The problem is usually the result of an improper shutdown, in this case while the external drive was attached and usually doing a proper shutdown will fix it but sometimes running a filesystem check is necessary.  You can do that from windows with the command:  chkdsk on the bad drive since it is a windows ntfs partition.  You might google this to get the correct parameters for the command as I don't use windows and can't make any suggestion.

---

### Post by Impavidus on 2014-06-18
> **yancek said:**
> Does that mean if you have the corrupted drive attached when you boot windows 8 you have problems?  What happens?  Did you try attaching the bad drive after booting windows 8?  I don't see how even having a bad data partition on a secondary drive would do that.  More details might help.A virus could do that, in theory.

Try to mount read-only, copy the files to an external drive, format the data drive and run a virus check on the recovered files.

---

