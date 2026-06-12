---
title: "Monitor GPU load? (htop, conky, etc)"
date: 2008-06-15
forum: General Help
---

### Post by kung fu buntu on 2008-06-15
Is there any monitor that can track GPU load?

I'm using the GPU to do some heavy math and would like to have an idea of the load usage... and be possible to compare it with the CPU load as well.

htop is very nice and from what I saw conky is great too (still have to try it)... but I haven't found anything for GPU

---

### Post by pb_online on 2008-06-15
I have ATI Graphics Card.

I can see the GPU load with...

```
sudo aticonfig --lsp
```

At first, the setting was by default on the full load (number 3) and the laptop gets very hot.

Now, I use ...

```
sudo aticonfig --set-powerstate=1
```

so I set the load to number 1. The temp of CPU felt down about 20 degrees.

---

### Post by kung fu buntu on 2008-06-15
nVidia card over here.

By running nvidia-settings I can get the GPU temperature, 60ºC at the moment.
There is no info about GPU load. I should update my nvidia packages, maybe there is something new.

Thanks for your post, it enlightened me on where to look for this information.

Any other nvidia users? :p

---

### Post by kung fu buntu on 2008-06-19
*bump*

Any nvidia users that know how to monitor GPU load?

---

### Post by sdennie on 2008-06-19
I'm not sure there is a way to directly do this on nvidia (in fact, I'm not even sure if it's an answerable question at all).  You may only be able to infer this based on CPU load or temperature.  Though, I could be wrong.

---

### Post by martimcfly on 2009-04-08
You can try gkrellm, it has many options and a nice gui
sudo apt-get install gkrellm2

---

### Post by alexcckll on 2011-03-18
Would be nice to get it into System Monitor as well though.. 
I could then track GPU process load on my netbook easily - and compare at a glance to CPU load.

---

### Post by youssef.barhomi on 2012-12-16
Hey, if you are still looking for this, you may check this out: [https://developer.nvidia.com/nvidia-management-library-nvml](https://developer.nvidia.com/nvidia-management-library-nvml)

Also, there is python bindings for it. I have used it and it gets you almost all variables you need from a gpu. If someone can write somethign similar to htop where you can show real time graphs on load, tempoerature, memory being used using ssh accross many machines, that would be fantastic. I'd probably start working on it if I can't find anything like it online since I have to manage many gpus for a high performance computing project.

---

### Post by Nick8 on 2012-12-16
If you have an NVIDIA card, Conky can monitor it.

Add the following to ~/.conkyrc

nvidia [threshold] [temp] [ambient] [gpufreq] [memfreq]

'threshold' Gives the thresholdtemperature at which the gpu slows down
'temp' Gives the gpu current temperature
'ambient' Gives current air temperature near GPU case
'gpufreq' Gives the current gpu frequency
'memfreq' Gives the current mem frequency

I haven't tested this, since I have Intel integrated graphics.

---

