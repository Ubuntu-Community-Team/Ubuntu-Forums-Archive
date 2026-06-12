---
title: "Installing netbeans"
date: 2008-01-10
forum: General Help
---

### Post by basketballer on 2008-01-10
I've installed JDK 1.6 and it was successfully installed
Then  when i came to install netbeans, it says that it can't find the JDK
although it is there in the directory /root/

what should i do ? Where should i place the JDK in order for netbeans to see it
Thanks in advance

---

### Post by jespdj on 2008-01-10
Is your JDK installed in the directory /root? That's strange. How did you install the JDK?

Instead of downloading and installing the JDK from Sun's website, install it from the Ubuntu repository. The newest version (1.6.0 update 3) is available in the Ubuntu repository.
```
sudo apt-get install sun-java6-jdk
```

---

### Post by basketballer on 2008-01-10
hmm i think maybe bcoz i worte first
sudo -i
then
chmod +x name.bin
sh name.bin

I believe i shouldn't have entered sudo -i

Thanks, i'll fix that, or i'll just get the one in repositories.

---

### Post by basketballer on 2008-01-10
O.K one more thing, 
i decided to get the one in the reposetories 
How can i remove the one in /root ?? Thanks again

---

