---
title: "Need to enable in software sources proprietary drivers to install nvidia driver ?"
date: 2020-08-03
forum: General Help
---

### Post by aug7744 on 2020-08-03
Is need enable in Software Sources Ubuntu Software Proprietary drivers for devices restricted additional drivers using Nvidia driver Metapackage from nvidia-driver-440 after apply changes to allow install downloaded drivers from nvidia or only need using command line ?

---

### Post by CelticWarrior on 2020-08-03
Open Software & Updates.

In the first tab make sure all but source code are selected.
Then, on the 5th tab - Additional Drivers - select and apply the recommended version. Typically it's all it takes. However, make sure the recommended version is actually the same as recommended by Nvidia in their website (use the website to check for the driver version only, do NOT install from Nvidia binaries).

---

### Post by aug7744 on 2020-08-05
I have tried and not works. The system is offline.
Because avoid the driver from nvidia site ?

---

### Post by CelticWarrior on 2020-08-05
Please bring the system online. Again, what it needs to download is negligible even in a metered connection.
It's absurd and very likely above your current knowledge to do it entirely offline. I would have to search a lot for the exact packages to download. for instance.

---

### Post by aug7744 on 2020-08-06
In windows the use simply download the driver run the setup and is ready to use.
Much patience need to install.
Since the begin I had knowledge that using ADDITIONAL DRIVERS is more simple than download from nvidia site.
I had selected exactly USING DRIVER METAPACKAGE FROM NVIDIA DRIVER 450 OPEN SOURCE and the download process was 100 % completed and after had another task that done 100 % ( (perhaps insatalling the files ? ).
After the system was idle for an long time and nothing of any task or window message if was or not installed the driver.
After several minutes I had restarted the system.
Now the system is using vga default driver and when I open ADDITIONAL DRIVER not is possible select the latest driver version being only possible to select 440 !
If I try to select the 450 version not have any chance to select because APPLY CHANGES not is displayed to select, but if selecting 440 APPLY CHANGES is displayed to select !
Almost 200 MB download for that driver and others more of 250 MB to test only two simple text editor. My access is metered and I need to avoid that type of problem.
Much patience to use Linux .... much even ...
If the solution to fix is download the 440 version and after the current 450 not way for me.

Another detail I had tried to install the nvidia driver proprietary and the installation not continue with message with have an nvidia kernel loaded in system.
An nvidia kernel loaded, but is using vga compatible driver.
Patience.

---

### Post by mastablasta on 2020-08-06
what GPU do you have?

for 450 version you would need to add PPA. 

even on windows you have to download the driver in some way to install it. and if you use some connection which can loose packages (e.g. wi-fi, phone connection) you could end up re-downloading it. using chips that offer opensource drivers (Intel, AMD) avoids this issue altogether since drivers are already in kernel and do not have to be downloaded afterwards.

---

### Post by CelticWarrior on 2020-08-06
> **aug7744 said:**
> 
Almost 200 MB download for that driver and others more of 250 MB to test only two simple text editor. My access is metered and I need to avoid that type of problem.
Much patience to use Linux .... much even ...
If the solution to fix is download the 440 version and after the current 450 not way for me.


The same driver version for Windows is **561.45MB**: [https://www.nvidia.es/Download/driverResults.aspx/162245/es](https://www.nvidia.es/Download/driverResults.aspx/162245/es)

---

### Post by aug7744 on 2020-08-06
@mastablasta "what GPU do you have?" GeForce GT 640  "for 450 version you would need to add PPA." was done before of downloading using additional drivers  "The same driver version for Windows is 561.45MB: https://www.nvidia.es/Download/drive...aspx/162245/es" I say simply an reply to say that need avoid download wrong software. Not speaking bad about Linux, but waiting to see if any developer or distro creator can read my post.

---

### Post by mastablasta on 2020-08-08
> **aug7744 said:**
> @mastablasta "what GPU do you have?" GeForce GT 640  "for 450 version you would need to add PPA." was done before of downloading using additional drivers 

last version that supports GT640 is 3.90 something.

What's a legacy driver: [https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/](https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/)

> 
**The 390.xx driver supports the following set of GPUs.**
GeForce GT 640           124B
 

Support timeframes for Unix legacy GPU releases: [https://nvidia.custhelp.com/app/answers/detail/a_id/3142](https://nvidia.custhelp.com/app/answers/detail/a_id/3142)

---

### Post by aug7744 on 2020-08-13
Thanks for all replies :)

---

