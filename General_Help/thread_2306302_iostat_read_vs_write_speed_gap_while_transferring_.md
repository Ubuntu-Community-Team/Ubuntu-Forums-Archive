---
title: "iostat read vs write speed gap while transferring data via Ethernet to SATA disk"
date: 2015-12-14
forum: General Help
---

### Post by Takisa on 2015-12-14
While reading 1.5 GB video file from SATA disk over Gigabit Ethernet *iostat* was used to profile IO performance.

Below are two short screenshots for data reading and data writing, respectively:

READ:
Device:         rrqm/s     wrqm/s     r/s     w/s     **rkB/s**     wkB/s     avgrq-sz     avgqu-sz     **await**     r_await     w_await     svctm     **%util **    
sda 0.00        0.00          78     0        **39936**    0            1024           0.10            **1.28**       1.28          0.00          1.28        **10.00**  
                                                                                                                                                                    
Device:         rrqm/s     wrqm/s     r/s     w/s     **rkB/s**     wkB/s     avgrq-sz     avgqu-sz     **await**     r_await     w_await     svctm     **%util**  
sda 0.00        0.00          79     0        **40960**   0             1036           0.12            **1.52**       1.52          0.00          1.52        **12.00**
                                                                                                                                                                                
Device:         rrqm/s     wrqm/s     r/s     w/s**     rkB/s**     wkB/s     avgrq-sz     avgqu-sz     **await**     r_await     w_await     svctm     **%util ** 
sda 0.00        0.00         75     0         **37888**    0            1010          0.05**             0.67**       0.67          0.00           0.67       **5.00**
                                                                                                                                                                                
Device:         rrqm/s     wrqm/s     r/s     w/s     **rkB/s**     wkB/s     avgrq-sz     avgqu-sz     **await**     r_await     w_await     svctm     **%util ** 
sda 0.00 0.00         78      0        **39936**   0             1024           0.11            **1.41**       1.41         0.00            1.41       **11.00**

WRITE:
Device:         rrqm/s     wrqm/s     r/s     w/s     rkB/s     **wkB/s**     avgrq-sz     avgqu-sz     await     r_await     **w_await**     svctm     **%util**  
sda               0.00        0.00         0        56      0           **28164**     1005           6.90            **74.46**     0.00          74.46        5.36        **30.00**

Device:         rrqm/s     wrqm/s     r/s     w/s     rkB/s     **wkB/s**     avgrq-sz     avgqu-sz     await     r_await     **w_await**     svctm     **%util**  
sda               0.00        0.00         0        97      0           **49664**     1024           26.32          **299.69**   0.00         299.69       4.64        **45.00**

Device:         rrqm/s     wrqm/s     r/s     w/s     rkB/s     **wkB/s**     avgrq-sz     avgqu-sz     await     r_await     **w_await**     svctm     **%util**  
sda               0.00        0.00         0        25      0           **12800**     1024           12.45          **88.00**     0.00         88.00         6.80        **17.00**

Device:         rrqm/s     wrqm/s     r/s     w/s     rkB/s     **wkB/s**     avgrq-sz     avgqu-sz     await     r_await     **w_await**     svctm**     %util ** 
sda               0.00         0.00         0       91      0           **46592**     1024           14.61          **273.30**   0.00          273.30      3.52        **32.00**

As you can see there are obvious problems with the write performances.

Here are *perf* block IO count reports:
READ:
Performance counter stats for 'system wide':
 
              **4304**      block:**block_touch_buffer**                                [100.00%]
                **24**        block:**block_dirty_buffer**                                  [100.00%]
                 0         block:block_rq_abort                                       [100.00%]
                12        block:block_rq_requeue                                  [100.00%]
              2948      block:block_rq_complete                                 [100.00%]
              2950      block:block_rq_insert                                       [100.00%]
              2967      block:block_rq_issue                                       [100.00%]
                 0         block:block_bio_bounce                                  [100.00%]
                 0         block:block_bio_complete                               [100.00%]
                21        block:block_bio_backmerge                            [100.00%]
                 0         block:block_bio_frontmerge                            [100.00%]
              2959      block:block_bio_queue                                   [100.00%]
              2938      block:block_getrq                                            [100.00%]
                 0         block:block_sleeprq                                        [100.00%]
              **2838**      block:**block_plug**                                             [100.00%]
              **2838**      block:**block_unplug**                                         [100.00%]
                 0         block:block_split                                             [100.00%]
               122       block:block_bio_remap                                   [100.00%] 
                 0         block:block_rq_remap 
 
      39.816748999 seconds time elapsed 

WRITE:
Performance counter stats for 'system wide':


            **224248**        block:**block_touch_buffer**                                   [100.00%]
            **359068**        block:**block_dirty_buffer**                                     [100.00%]
                 0             block:block_rq_abort                                         [100.00%]
                53            block:block_rq_requeue                                     [100.00%]
              2935          block:block_rq_complete                                    [100.00%]
              2975          block:block_rq_insert                                         [100.00%]                                                                                  
              2998          block:block_rq_issue                                         [100.00%]
                 0             block:block_bio_bounce                                    [100.00%]
                 0             block:block_bio_complete                                  [100.00%]
                70            block:block_bio_backmerge                               [100.00%]
                 0             block:block_bio_frontmerge                               [100.00%]
              2994          block:block_bio_queue                                      [100.00%]
              2924          block:block_getrq                                               [100.00%]
                 0             block:block_sleeprq                                           [100.00%]
               **249**           block:**block_plug**                                                [100.00%]
               **249**           block:**block_unplug**                                            [100.00%]
                 0             block:block_split                                                 [100.00%]
                91            block:block_bio_remap                                      [100.00%] 
                 0             block:block_rq_remap
 
      54.917482330 seconds time elapsed 


My Ubuntu version is linaro utopic 14.10.

Since I'm new in this field, can any of you with the help of your higher "intuition" :) provide me some clues in the direction I should go in order to find out why write procedure has drastically lower performance.

Thanks

---

### Post by sammiev on 2015-12-14
The first item noticed is that [14.10]("http://www.ubuntu.com/info/release-end-of-life") is expired.

You should move onto a LTS version.

---

### Post by Takisa on 2015-12-14
Okay, that's true. But, I need to stick with this one.

---

### Post by coffeecat on 2015-12-14
Not an Ubuntu, Linux and OS Chat thread.

*Thread moved to **General Help**.*

> **Takisa said:**
> Okay, that's true. But, I need to stick with this one.

Why?

Ubuntu 14.10 is no longer supported, which means there are no more updates or security/bug fixes. You would do better installing a supported version and seeing if your problem persists.

---

### Post by Takisa on 2015-12-15
Well, yes, you got the point, but this is project specification, something I can't influence.

I was hopping to some guidelines, simple thoughts that could lead me in some specific direction (other than, switch to newer version :) ).

Thanks

---

