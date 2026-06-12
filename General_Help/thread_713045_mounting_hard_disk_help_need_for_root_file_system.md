---
title: "mounting hard disk help need for root file system"
date: 2008-03-02
forum: General Help
---

### Post by leebra on 2008-03-02
hi every one this is my first post and its for help. i have just installed Ubuntu 7.10 on a 2.1G hard disk which is now full. i have two more hard disk but do not know where to mount them.

---

### Post by scragar on 2008-03-02
I would definatly recomend mounting one as your home folder, since this is essential if you ever need to reinstall.

---

### Post by leebra on 2008-03-02
i will be making a /home mount point but where do all the updates and programs go

---

### Post by leebra on 2008-03-02
i need to know because i can no longer update or add programs

---

### Post by Omnios on 2008-03-02
Hi some more information on you other hard drives might help. 
 
By default you root directory / is where everything is installed. / is where all the system "program" stuff goes. It also contains the /home directory in t where all your personl files go. You can mount /home on a seperate partition which leaves only system files on root /. Noww with /home on a seperate partition in affect all your personal files will be in the /home partition. Also by having a /home partition the root / can be very small and moving your /home files to the new partiton will allow more rooms for installing and updating updates etc.

---

### Post by leebra on 2008-03-02
my two other disks are only 4.5G with a 512mb swap and a 1.4G disk with a 256mb swap

---

