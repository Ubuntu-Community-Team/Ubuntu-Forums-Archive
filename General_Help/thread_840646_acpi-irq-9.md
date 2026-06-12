---
title: "acpi-irq-9"
date: 2008-06-25
forum: General Help
---

### Post by asharness on 2008-06-25
I have a e-machine,with a duel core 3.2 with 1 gig ram and no matter what i try, I am still having a problem with irq and apci. They are constantly running at 30+ %. I have a second hd for ubuntu and wondering if that could cause this. heres the top log. any idea would be great. Ive already tryed changing kernal line to irqpoll, apci=force and one other with no improvment

       72 root     -51  -5     0    0    0 S   30  0.0   3:15.38 IRQ-9              
   71 root      15  -5     0    0    0 R   11  0.0   1:07.41 kacpi_notify       
   70 root      15  -5     0    0    0 R    8  0.0   0:53.24 kacpid             
 5836 root      20   0  381m  34m 7136 R    7  3.4   0:18.19 Xorg               
 6230 scott     20   0  168m  75m  19m S    2  7.6   0:49.02 firefox            
 6269 scott     20   0 78124  21m  10m S    1  2.1   0:02.04 gnome-terminal     
 6183 scott     20   0 22472  14m 5920 S    1  1.5   0:05.48 compiz.real        
    6 root     -51  -5     0    0    0 S    0  0.0   0:02.01 softirq-timer/0    
   24 root     -51  -5     0    0    0 S    0  0.0   0:00.88 softirq-sched/1    
  828 root     -51  -5     0    0    0 S    0  0.0   0:00.27 IRQ-12             
 1389 root     -51  -5     0    0    0 S    0  0.0   0:00.20 IRQ-19             
 6118 scott     20   0 40480  21m  12m S    0  2.2   0:03.67 gnome-panel        
 6289 scott     20   0  2308 1136  852 R    0  0.1   0:01.45 top                
    1 root      20   0  2844 1692  544 S    0  0.2   0:01.21 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      RT  -5     0    0    0 S    0  0.0   0:00.00 posix_cpu_timer

---

