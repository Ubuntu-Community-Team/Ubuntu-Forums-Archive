---
title: "Encrypted File SYstem"
date: 2006-10-27
forum: General Help
---

### Post by timhaughton on 2006-10-27
I had a dmcrypt encrypted disk using dmcrypt under dapper. This makes use of /dev/mapper, which doesn't seem to be there under Edgy. Help ! :)

Cheers,

Tim

---

### Post by kidders on 2006-10-27
Hi there,

I've only ever used dmcrypt with Gentoo, but I had to create the /dev entries myself with **devmap_mknod.sh** (which should be provided with the dmcrypt package). Be careful to run it just once though.

Any luck?

---

### Post by timhaughton on 2006-10-27
Seems I was a little premature. I don't think I had to do it with Dapper, but a reboot seems to have created the mapper.

Cheers,

Tim

---

### Post by kidders on 2006-10-27
Kewl. The installer may have rewritten your udev rules. You may have just needed to re-parse them.

Glad you solved your problem :-)

---

