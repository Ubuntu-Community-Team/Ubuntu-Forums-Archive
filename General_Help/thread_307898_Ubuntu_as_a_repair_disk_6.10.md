---
title: "Ubuntu as a repair disk? 6.10"
date: 2006-11-27
forum: General Help
---

### Post by Fnordle on 2006-11-27
I've been trying to use Ubuntu 6.10 as a repair disk for damaged Windows installs - mounting the NTFS as read-only, copying data to a share then re-installing.  Unfortunatley the latest build of 6.10 RC1 seems to make doing so no longer possible.

1. I can find no GUI mount options.  I am sure there used to be one, but it's gone now.  I can mount manually but only with SUDO (so normal users cannot access the volume).

2. After mounting I can only access the volume with SUDO NAUTILUS.  Clicking a dragging to a network share doesn't work.  Not really a surprise as the share is on a different user (non sudo).

3. Starting another SUDO NAUTILUS will not allow me to access any network shares.  Only a normal user can do it - root cannot.

I don't think I am doing anything wrong, and don't know what else to try.  Maybe its a bug?  I have tried it on 2xLaptops, 1xDesktop and VMWare, all with exactly the same result.

---

### Post by der_joachim on 2006-11-27
Try [Knoppix]("http://www.knoppix.org/"). It is much better for system restores. Amongst others, it has NTFS mounting out of the box and a partition editor.

---

### Post by Fnordle on 2006-11-30
Maybe.  It seems a little strange that it always used to be possible but now isn't - a bit of a step backwards imo.  Is it a known bug that 6.10 cannot browse Samba shares as root?

---

