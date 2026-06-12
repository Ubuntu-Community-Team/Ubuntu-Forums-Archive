---
title: "Ubuntu 16.04 LTS on Alienware 15 Laptop"
date: 2017-07-12
forum: General Help
---

### Post by h45h3m1 on 2017-07-12
Hello,

I recently purchased an Alienware 15 laptop for work. The specifications of the laptop:

CPU: 7th Generation Intel® Core™ i7-7700HQ

Operating System: Windows 10 Home 64-bit English

Memory: 16GB DDR4 at 2400MHz

GPU: NVIDIA® GeForce® GTX 1060 with 6GB GDDR5 – 78W

My work requires Ubuntu 16.04 LTS. Our IT team was able to put this  version of Ubuntu on the laptop (with Unity Desktop Environment),  however it was not at all straight forward and the laptop runs very slow  overall. 
 
 Does anyone have any experience/advice for installing Ubuntu 16.04 LTS  on an Alienware 15 laptop? Are specific Desktop Environments better  suited for this laptop?   
 
Thanks!

---

### Post by jim_deadlock on 2017-07-12
With that kind of power you can run any desktop you like, it's down to your personal preference.

---

### Post by Autodave on 2017-07-12
First thing I have to ask is whether the correct video driver was  installed.  Got to Settings -> Additional Drivers and see if it  recommends a different driver than what you are using. If it does  recommend a different one, you need to install it and go from there. 

The 375.66 driver is what Nvidia's site is calling the latest stable driver. That should be the one installed.

---

### Post by h45h3m1 on 2017-07-12
Thanks for the response. I currently have the recommended NVIDIA driver 375.66 installed and used.

---

### Post by mastablasta on 2017-07-13
it was not all straight forward because of hardware incompatibility (hardware was made to run with windows only) which is also causing it to run slow overall. we also have no idea what special setting you or they have used during install. for example, nVidia on laptops nowadays usually uses Optimus technology which is not supported in linux. however a project called bumblebee can help but user will have to manually switch between the GPUs. was that installed and configured propperly?

next, in /var/log will be system logs. Linux logs everything. there is also a log viewer installed by default. look through the logs and post any errors you may encounter or paste them into google to see if anyone else with same issue found a solution.

then also check system resources usage.  there is a GUI app for that but i suggest you also run a terminal application called top or htop (the latter needs to be installed). check which process is taking up the resources and post the result here or use it to search for a solution online.

what are you doing on Ubuntu? if it is not something graphically intensive an easier and better way would be to install it inside a virtualbox (or similar VM). you certainly have the specs for it.: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

If the laptop is relatively current you migth want to install 17.04 instead of 16.04. the 17.04 version will have a newer kernel. i am not sure the kernel made it to 16.04 yet. when using 16.04 make sure you have the one with latest possible kernel. in linux (unlike in windows) most drivers are found in kernel, so newer kernel= newer drivers and newer driver=[usually] better hardware support for new hardware.

---

