---
title: "shared RAM with nvidia GPU , is it possible?"
date: 2022-08-01
forum: General Help
---

### Post by habernir on 2022-08-01
hello their

in windows their is "shared GPU memory"
just want to know if it possible to do the same in ubuntu.
is it possible?

---

### Post by grahammechanical on 2022-08-01
It all depends on what video adapter you have. Some video adapters come with their own amount of video memory. They are called discrete adapters. Some video adapters are integrated adapters. They use some of the system memory (RAM). The computer operating system has no choice. It has to use the hardware present in the machine. The video adapter through the video driver will force Ubuntu to share RAM with the video adapter.

Regards

---

### Post by habernir on 2022-08-01
the card that i have its NVIDIA 3080
and the purpose for this its for rendering .

is it possible to force ubuntu to share ram?

---

### Post by TheFu on 2022-08-01
It isn't a Windows thing. It is a hardware/BIOS thing.  Typically, iGPUs like those from Intel will take some RAM for the iGPU needs. Some BIOSes allow control over the amount of RAM used.  I've seen 256MB to 1G of RAM stolen by laptops to be used for by the iGPU.

Or am I missing the goal?  Are you hoping to install an 8GB DDR5 GPU and take 50% of that very expensive RAM for use by the CPU to run programs?
Beware that addon GPUs are connected by PCIe slots with limited bandwidth.  Memory installed on the motherboard is designed with a much greater bandwidth for access by the CPU than any PCIe slot can touch.
[https://www.reddit.com/r/hardware/comments/1e6kbc/memory_bandwidth_cpu_vs_pcie/](https://www.reddit.com/r/hardware/comments/1e6kbc/memory_bandwidth_cpu_vs_pcie/) has useful comments, I think.

In short, if you want to use GPU RAM, you'll want to create a program that gets run on the GPU specifically to avoid dealing with the PCIe controller bottleneck.  Nvidia has lots of tools for this. The GPU processors are not general purpose. They are designed for highly parallel workloads - typically for 384-10752 cores.  For single-threaded programs, sticking with the normal CPU makes 1000x more sense.

[https://developer.nvidia.com/cuda-gpus](https://developer.nvidia.com/cuda-gpus) looks like a starting place.

---

### Post by #&amp;thj^% on 2022-08-01
> **TheFu said:**
> 
In short, if you want to use GPU RAM, you'll want to create a program that gets run on the GPU specifically to avoid dealing with the PCIe controller bottleneck.  Nvidia has lots of tools for this. The GPU processors are not general purpose. They are designed for highly parallel workloads - typically for 384-10752 cores.  For single-threaded programs, sticking with the normal CPU makes 1000x more sense.

[https://developer.nvidia.com/cuda-gpus](https://developer.nvidia.com/cuda-gpus) looks like a starting place.
+1 I was about to post:
 I don't know if there is a way to **"extend"** the GPU memory. I don't think the GPU can use pinned memory that is bigger than its own, but I am not certain.
So it's not a matter if there is possible or not, **it's a matter of performance when doing it**.
 A well designed software will use the GPU near its output FLOPS limits, while one designed badly will not. Usually the computing and hashing software comes in the 1st category. Same goes for allocating VRAM.
I can't imagine the OP running short rendering though this is my guess on his specs:
```
Memory Size 	12 GB 	12 GB / 10 GB
Memory Type 	GDDR6X 	GDDR6X
```

---

### Post by habernir on 2022-08-01
in windows in task manager its write me "[COLOR=#000000]shared GPU memory" = 64GB ( i have 128GB ram) 
and believe me the shared GPU memory working greate . 

and i dont have any other video card just 3080 .
my  motherboard msi x570 ace.

if i understand you its seem thats "[/COLOR][COLOR=#000000]shared GPU memory" can only be in windows  and not in linux.
[/COLOR][COLOR=#000000]too bad but thanks anyway for your help

and about the preformace. well i have **_alittle _**memory leak from vram to ram in windows when rendering sooo i dont have an impact in the performance .


[/COLOR]

---

### Post by TheFu on 2022-08-01
[https://forums.developer.nvidia.com/t/shared-system-memory-on-linux/41466/4](https://forums.developer.nvidia.com/t/shared-system-memory-on-linux/41466/4) says:
> I believe you may be a little confused as to what Windows “system shared memory” is (there is no such thing with that name, and for a very long time our GPUs have been able to “spill” in system memory when video memory is exhausted, on Windows as well as on Linux).
In the situation you describe the behavior is expected - just because you’re starting a new application doesn’t mean that other applications will “make room” for it (why would they). Once the VRAM limit is reached, the driver behavior will be a mix of evicting video memory not currently in use and spilling to system memory.
Either way if the game “fails and gets stuck”, it’s an application bug.

Need to be more exact with terms.  vRAM and RAM are different physical things.  

[https://graphicscardsadvisor.com/how-to-use-whole-ram-in-linux-for-gpu/](https://graphicscardsadvisor.com/how-to-use-whole-ram-in-linux-for-gpu/) has some Linux specifics too. I didn't see anything that contradicts what's in responses above.

---

### Post by habernir on 2022-08-02
> **TheFu said:**
> [https://forums.developer.nvidia.com/t/shared-system-memory-on-linux/41466/4](https://forums.developer.nvidia.com/t/shared-system-memory-on-linux/41466/4) says:


Need to be more exact with terms.  vRAM and RAM are different physical things.  

[https://graphicscardsadvisor.com/how-to-use-whole-ram-in-linux-for-gpu/](https://graphicscardsadvisor.com/how-to-use-whole-ram-in-linux-for-gpu/) has some Linux specifics too. I didn't see anything that contradicts what's in responses above.
well i know thats gpu doesn't have direct access to the ram .
and correct me if i wrong BUT in windows  when vRAM is out-of memory its start populating the ram (for future use by GPU) **_and yes i know that the gpu doesn't have direct access to the ram_** but it doesn't conflict with that another process will do the job for the gpu and when the gpu will need this data the process will move it back.
and yes you cannot call it that "shared RAM" in the full sense of the word  BUT the purpose of the idea its the same.

the bottom line i just want to ask if it possible to do the some **_technique_** such as "shared GPU memory" in windows (you can see it in Task manager-->performance--->GPU 0) 
i dont know if microsoft do it by buffer or by other process .....or something else......
the bottom line i just want to know if it can be done in linux

and i need it because
and when i try to render in ubuntu or other distro its always failed
but when itry to render the same scene in windows its always succeed because of the "shared GPU memory technique thats  windows have

and people tell me why do i need using RAM (because their is a cost of performce) 
welll the reason for it when you render only the CPU as you know its very very slow but when you render CPU+GPU its render really fast even with the cost of performce ,
and you can see it when i render in windows and linux.

and if I got this all wrong please correct me.

---

### Post by miguel001 on 2022-08-02
> **habernir said:**
> but when itry to render the same scene in windows its always succeed because of the "shared GPU memory technique thats  windows have

I wish that I could say that's true but that's definitely not lol. You should come up with some other reason.

Shared memory is only an integrated GPU thing and it changes not with Linux or Windows. Its all the way down to the board and APU/iGPU level. The OS - even Linux - has to deal with it and use it. It doesn't magically become dedicated GPU memory.

Get off this train :)

---

### Post by TheFu on 2022-08-02
A feature that I've seen is that programs loaded into the GPU, but aren't active, should be swapped out to system RAM so the GPU has more vRAM available for the active programs.  I searched for anything specific to enable this in Linux, but didn't find much and nothing within the last 5 yrs that was for nvidia. There were a few posts for AMD GPUs and BIOS settings.  I looked across multiple distros.  The results I found were very low quality articles, as though someone thought s/windows/linux/ would be helpful.  It clearly isn't.  The link I added above is one of those, sorry. The other link is relevant. 

I suspect my web searched failed because I have the wrong technical terms for this specific feature.

Maybe posting a clear question to the nVidia support or developer's forum,  including the kernel and GPU driver versions would yield better results?  Perhaps the nvidia-smi output and using the  bug-reporting tool included with the nvidia drivers/tools, nvidia-bug-report.sh. Running these commands when the vRAM is very full would be helpful to the forum members over there.  But I really don't know.

---

### Post by #&amp;thj^% on 2022-08-02
> **TheFu said:**
> 
Maybe posting a clear question to the nVidia support or developer's forum,  including the kernel and GPU driver versions would yield better results?  Perhaps the nvidia-smi output and using the  bug-reporting tool included with the nvidia drivers/tools, nvidia-bug-report.sh. Running these commands when the vRAM is very full would be helpful to the forum members over there.  But I really don't know.
+1

Ok, there is a shared mem slot IE:
Mine shows:
```
cat /proc/sys/kernel/shmmax
18446744073692774399
```
Now i need to see all:
```
ipcs -m 

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x00000000 25         me         600        4096       2          dest         
0x00000000 32         me         600        57344      2          dest         
0x00000000 33         me         600        53248      2          dest         
0x00000000 44         me         600        524288     2          dest         
0x00000000 46         me         600        2097152    2          dest         
0x00000000 32816      me         600        102400     2          dest         
0x00000000 32817      me         600        102400     2          dest         
0x00000000 32818      me         600        1126400    2          dest         
0x00000000 32819      me         600        1126400    2          dest         
0x00000000 32822      me         600        28672      2          dest         
0x00000000 32823      me         600        28672      2          dest         

```
This looks to me like it's possible on Linux. (Again I'm not certain)
But it would have to written to that application

I remember when I first touched Linux this was around 2005-2006, 
/dev/shm is nothing but implementation of traditional shared memory concept. It is an efficient means of passing data between programs. One program will create a memory portion, which other processes (if permitted) can access. This will result into speeding up things on Linux.
so if I dig a bit deeper on Process's I'll look at:
```
ipcs -pm 

------ Shared Memory Creator/Last-op PIDs --------
shmid      owner      cpid       lpid      
25         me         1399       2799      
32         me         26138      113924    
33         me         26138      113924    
44         me         87273      902       
46         me         87273      902       
32816      me         26138      113924    
32817      me         26138      113924    
32818      me         26138      113924    
32819      me         26138      113924    
32822      me         26138      902       
32823      me         26138      902       


```
[list]
    [*]cpid is the process ID of the job that created the shared memory segment.
    [*]lpid is the process ID of the last job to attach or detach from the shared memory segment or change the semaphore value.
[/list]
If i run say 7-10 VM's at one time, and no use of any GUI's I'm fine, but if i bring GUI's into the Mix I need some help there.
For this something like this should and does help IE:

you will give your tmpfs instance on /disk2/tmpfs which can allocate 5GB RAM/SWAP in 5K inodes and it is only accessible by root: These are just general name sake, so adjust to your specs/devs
```
# mount -t tmpfs -o size=5G,nr_inodes=5k,mode=700 tmpfs /disk2/tmpfs
```
Now this is a lot of information to absorb, and if I wanted to make the above permanent, i would add it to fstab.
```
none      /dev/shm        tmpfs   defaults,size=8G        0 0
```
But for my KVM's I'll only use it per session and not persistent.
All this leads to A very advanced user, and the application/software used.

---

### Post by habernir on 2022-08-02
> **miguel001 said:**
> I wish that I could say that's true but that's definitely not lol. You should come up with some other reason.

Shared memory is only an integrated GPU thing and it changes not with Linux or Windows. Its all the way down to the board and APU/iGPU level. The OS - even Linux - has to deal with it and use it. It doesn't magically become dedicated GPU memory.

Get off this train :)
yes you right the "shared GPU memory" in windows its just the cache and Shared memory its only for integrated GPU.

but the problem that i have its very very strange . 
because when rendering in windows its above my vRAM (and the render engine its doesn't support out-of-core) soo its supposed to fail but not and windows its less efficienct than linux.
and its linux that its more efficientct  (OS using less vRAM) its failing all the time.

soo the only reason i can think its nvidia drivers .

and thanks again for you time.

---

### Post by habernir on 2022-08-03
> **1fallen said:**
> +1

Ok, there is a shared mem slot IE:
Mine shows:
```
cat /proc/sys/kernel/shmmax
18446744073692774399
```
Now i need to see all:
```
ipcs -m 

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x00000000 25         me         600        4096       2          dest         
0x00000000 32         me         600        57344      2          dest         
0x00000000 33         me         600        53248      2          dest         
0x00000000 44         me         600        524288     2          dest         
0x00000000 46         me         600        2097152    2          dest         
0x00000000 32816      me         600        102400     2          dest         
0x00000000 32817      me         600        102400     2          dest         
0x00000000 32818      me         600        1126400    2          dest         
0x00000000 32819      me         600        1126400    2          dest         
0x00000000 32822      me         600        28672      2          dest         
0x00000000 32823      me         600        28672      2          dest         

```
This looks to me like it's possible on Linux. (Again I'm not certain)
But it would have to written to that application

I remember when I first touched Linux this was around 2005-2006, 
/dev/shm is nothing but implementation of traditional shared memory concept. It is an efficient means of passing data between programs. One program will create a memory portion, which other processes (if permitted) can access. This will result into speeding up things on Linux.
so if I dig a bit deeper on Process's I'll look at:
```
ipcs -pm 

------ Shared Memory Creator/Last-op PIDs --------
shmid      owner      cpid       lpid      
25         me         1399       2799      
32         me         26138      113924    
33         me         26138      113924    
44         me         87273      902       
46         me         87273      902       
32816      me         26138      113924    
32817      me         26138      113924    
32818      me         26138      113924    
32819      me         26138      113924    
32822      me         26138      902       
32823      me         26138      902       


```
[LIST]
[*]cpid is the process ID of the job that created the shared memory segment.
[*]lpid is the process ID of the last job to attach or detach from the shared memory segment or change the semaphore value.
[/LIST]
If i run say 7-10 VM's at one time, and no use of any GUI's I'm fine, but if i bring GUI's into the Mix I need some help there.
For this something like this should and does help IE:

you will give your tmpfs instance on /disk2/tmpfs which can allocate 5GB RAM/SWAP in 5K inodes and it is only accessible by root: These are just general name sake, so adjust to your specs/devs
```
# mount -t tmpfs -o size=5G,nr_inodes=5k,mode=700 tmpfs /disk2/tmpfs
```
Now this is a lot of information to absorb, and if I wanted to make the above permanent, i would add it to fstab.
```
none      /dev/shm        tmpfs   defaults,size=8G        0 0
```
But for my KVM's I'll only use it per session and not persistent.
All this leads to A very advanced user, and the application/software used.

[[COLOR=#000000]1fallen[/COLOR]]("https://ubuntuforums.org/member.php?u=2040855") thanks for your help i read it and investigating it.
i dont think its the same as windows because the relationship between the process and the OS. 
soo because of that i dont think its possible to do the same way as windows

---

### Post by habernir on 2022-08-03
> **miguel001 said:**
> I wish that I could say that's true but that's definitely not lol. You should come up with some other reason.

Shared memory is only an integrated GPU thing and it changes not with Linux or Windows. Its all the way down to the board and APU/iGPU level. The OS - even Linux - has to deal with it and use it. It doesn't magically become dedicated GPU memory.

Get off this train :)

[COLOR=#000000] just do another rendering but this time i do it with another GPU rendering software and yes its fill the "shared GPU memory" in windows when the GPU vRam full (trust me i'm not dreaming)  soo something going on their.[/COLOR]
[COLOR=#000000]i also create hard rendering with another card (nvidia 3090) and its uses also "shared GPU memory" when its full.[/COLOR]

in ubuntu i have more free vRAM (as you know) than windows.
and still its fails in ubuntu to render 
BUT in windows i also open two 3d software and still its success to render in GPU (never fails)
and that's what makes it so weird and I have no idea why it's happening. 

[COLOR=#000000]and if the "shared GPU memory" its just for iGPU soo how is it possible that when i'm rendering its fill this section? and thats why i assumed before that may be its [/COLOR]controlled [COLOR=#000000]by OS internal process for the rendering software  BUT if its not [/COLOR]possible [COLOR=#000000]than what happening their? 
[/COLOR]thats what i want to know..
may be nvidia drviers issue?

---

### Post by TheFu on 2022-08-03
If the rendering is failing due to memory lack, perhaps render different layers separately?

---

### Post by Yellow Pasque on 2022-08-03
[https://forums.developer.nvidia.com/t/shared-system-memory-on-linux/41466/3](https://forums.developer.nvidia.com/t/shared-system-memory-on-linux/41466/3)

And if you still have questions, you would be better off asking on that forum.

---

