---
title: "How can I install an old version of a software"
date: 2018-03-30
forum: General Help
---

### Post by f76 on 2018-03-30
Hi!
I need to install an older version of cuda-toolkit. The current version is 9.1 and i need version 5.0 to be able to accelerate a program called freesurfer (that is not updating its gpu-acceleration thingy). The application needs libcudart5.0 . When looking for this older version i found on the nvidia homepage that it was used in the days of Ubuntu 11.10 and 10.04. 
They also provide a link to a ".run" file. 

My question: is there any way to install this older version via apt-get? Should i just get the ".run" file and run it?

Thanks!

---

### Post by monkeybrain20122 on 2018-03-30
Do not use the .run file. Nvidia provides a repository for cuda stuffs, once installed you will find different versions of cuda go to [https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604)
choose Ubuntu 16.04 >  deb (network) to download the .deb which when installed will create an entry in your sources list.


Edited: cuda 5.0 maybe too far back, the repository only has cuda 8, 9 and 9.1, sorry.

---

### Post by monkeybrain20122 on 2018-03-30
According to this [link]("https://github.com/freesurfer/freesurfer/issues/107") freesurfer works with cuda 8 and 9.1 if you build it from source with the proper paths.

---

### Post by f76 on 2018-03-30
I will try and see if I can learn to build from source - thank you

---

