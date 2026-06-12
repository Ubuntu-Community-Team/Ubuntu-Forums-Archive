---
title: "Extraction with 7z"
date: 2018-11-02
forum: General Help
---

### Post by Joe_Linux on 2018-11-02
I am trying to extract files with 7z and I am receiving the following error messages 

```
fred@fred-GA-78LMT-USB3:~$ 7z x STC_VOL1_BR.iso.zip.001

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,8 CPUs)


Error:
there is no such archive
fred@fred-GA-78LMT-USB3:~$ 7z x STC_VOL1_BR.iso.zip.002

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,8 CPUs)


Error:
there is no such archive
fred@fred-GA-78LMT-USB3:~$ 7z x STC_VOL1_BR.iso.zip

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,8 CPUs)


Error:
there is no such archive
fred@fred-GA-78LMT-USB3:~$ 7z x STC_VOL1_BR.iso

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,8 CPUs)


Error:
there is no such archive
fred@fred-GA-78LMT-USB3:~$ 7z x STC_VOL1_BR.iso

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,8 CPUs)


Error:
there is no such archive
fred@fred-GA-78LMT-USB3:~$ 7z x STC_VOL1_BR.iso.zip

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,8 CPUs)


Error:
there is no such archive
fred@fred-GA-78LMT-USB3:~$ sudo 7x x STC_VOL1_BR.iso.zip.001
[sudo] password for fred: 
sudo: 7x: command not found
fred@fred-GA-78LMT-USB3:~$ 
```
Thank you in advance

---

### Post by ajgreeny on 2018-11-02
Are you running the **7z x** command from the folder where the archives are sitting, which I assume is in your home folder?

Have you tried using command **unzip** instead of **7z** though I'm not sure if it's installed by default?

---

