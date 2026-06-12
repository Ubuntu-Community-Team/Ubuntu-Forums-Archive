---
title: "memtest"
date: 2007-01-15
forum: General Help
---

### Post by alftoo on 2007-01-15
Hi

I ran a memtest and really need some help with the output.

I got one block with 512 and one with 256.

Tst: 3
Pass: 0
Failing Address: 0001a4dd854 - 420.8MB
Good: 04040404
Bad: 040c0404
Err - Bits: 00080000
Count : 181
Chan :

It ran for about an hour. I would really like to know if it is the RAM before I get some new ones. If you need any other output from the memtest please say so.

Thanks

---

### Post by budgie9 on 2007-01-15
You may like to try all or  some of the following before you run out to spend more money.

1. Try reseating the memory in the m/board and try the tests again.
2. Swat the sticks about in the slots to see if the error comes back io the same location. This may indicare if one stick is faulty or it could be  sticks  not sitting in the slot correctly. 
3. Remove one stick completly and see if that reports an error. Then replace with the other stick. This should help you isolate a particular stick if one is failing.
4 if you have other memory slots try moving the sticks to them also.
Needless to say run the tests to see if it indicates a problem between each operation.
I would suggest you let the tests run for a while if they indicate all clear on the first run through.

If you can isolate a particular stick then you have the culprit and then you should replace it.

---

### Post by John Doe on 2007-01-15
[http://www.memtest86.com/#trouble](http://www.memtest86.com/#trouble) has info on troubleshooting memory errors.

Here is an excerpt of what that site says:
> 
Please be aware that not all errors reported by Memtest86 are due to bad memory. The test implicitly tests the CPU, L1 and L2 caches as well as the motherboard. It is impossible for the test to determine what causes the failure to occur. However, most failures will be due to a problem with memory module. When it is not, the only option is to replace parts until the failure is corrected.

Once a memory error has been detected, determining the failing SIMM/DIMM module is not a clear cut procedure. With the large number of motherboard vendors and possible combinations of memory slots it would be difficult if not impossible to assemble complete information about how a particular error would map to a failing memory module. However, there are steps that may be taken to determine the failing module. Here are four techniques that you may wish to use:

1) Removing modules
This is simplest method for isolating a failing modules, but may only be employed when one or more modules can be removed from the system. By selectively removing modules from the system and then running the test you will be able to find the bad modules. Be sure to note exactly which modules are in the system when the test passes and when the test fails.

2) Rotating modules
When none of the modules can be removed then you may wish to rotate modules to find the failing one. This technique can only be used if there are three or more modules in the system. Change the location of two modules at a time. For example put the module from slot 1 into slot 2 and put the module from slot 2 in slot 1. Run the test and if either the failing bit or address changes then you know that the failing module is one of the ones just moved. By using several combinations of module movement you should be able to determine which module is failing.

3) Replacing modules
If you are unable to use either of the previous techniques then you are left to selective replacement of modules to find the failure.


---

