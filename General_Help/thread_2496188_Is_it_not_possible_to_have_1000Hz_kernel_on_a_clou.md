---
title: "Is it not possible to have 1000Hz kernel on a cloud server like AWS?"
date: 2024-03-17
forum: General Help
---

### Post by forumate on 2024-03-17
Hello,

I read that the next release (24.04) will come with an option for "low latency" and will tick at 1000Hz: [https://discourse.ubuntu.com/t/enable-low-latency-features-in-the-generic-ubuntu-kernel-for-24-04/42255](https://discourse.ubuntu.com/t/enable-low-latency-features-in-the-generic-ubuntu-kernel-for-24-04/42255)

But then I was told that it won't work on a managed hypervisor like the one in AWS and I need dedicated server for this to work.

Is it true? If so, can you please explain in a more simple language why because I do not have deep OS knowledge.

Thank you

---

### Post by MAFoElffen on 2024-03-18
I haven't heard that "it will not work", but the Ubuntu AWS series or kernels is optimized for running on AWS Cloud...

RE:
[https://ubuntu.com/blog/introducing-the-ubuntu-aws-rolling-kernel-2](https://ubuntu.com/blog/introducing-the-ubuntu-aws-rolling-kernel-2)
[https://ubuntu.com/kernel/variants](https://ubuntu.com/kernel/variants)

The first link was the intro for the AWS Rolling Kernel Series when it cam out for 18.04.

The second link explains the differing Ubuntu Kernel Series types, and their intended purposes.

I am doing DEV Testing for Noble. At first, I, myself was concerned by their announcement of going to the low-latency kernel for all. I was, becaseu in Ubuntus doc's and the low-latency kernel, previous to that announcement, it said that it was targeted for applications that required it, and was discouraged for those that didn't as there were problems with some modules/drivers while using that kernel config... 

Then there was this:
> [INDENT]   These are some simple guidelines provided to help you understand which   kernel, and in which order, you should test to fit your use case.
      
[LIST]
[*]If you do not require low latency for your system then please use the -generic kernel. 
[*]If you need a low latency system (e.g. for recording audio) then  please use the -preempt kernel as a first choice. This reduces latency   but doesn't sacrifice power saving features. It is available only for   64 bit systems (also called amd64). 
[*]If the -preempt kernel does not provide enough low latency for your needs (or you have an 32 bit system) then you should try the   -lowlatency kernel. 
[*]If the -lowlatency kernel isn't enough then you should try the -rt kernel 
[*]If the -rt kernel isn't enough stable for you then you should try the -realtime kernel 
[/LIST]
 [/INDENT]

Which is explained in more detail here: [https://sevencapitalsins.wordpress.com/2007/08/10/low-latency-kernel-wtf/](https://sevencapitalsins.wordpress.com/2007/08/10/low-latency-kernel-wtf/)

BUT... Honestly, I haven't seen any problems with any of that while testing DEV Noble. So I'm really not sure yet if what was told to us in the past about that is real, or not. I guess time will tell.

But going back to AWS, the AWS kernel series is optimized for running on the AWS Cloud. Just as the AZURE series is optimized for running on the AZURE Cloud.

---

