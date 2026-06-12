---
title: "nanosleep verification"
date: 2015-08-13
forum: General Help
---

### Post by Vinayaka_Negalur on 2015-08-13
Hi,

I am back again with another problem.

I want to introduce a sleep of 10ms in my loop. But the sleep seems not working. I am using nanosleep in my code. I didn't find any post where the nanosecond was verified.
Since the 10ms timer was not working, I wanted to verify with 100ms. The log shows me sometimes it is ~80ms and sometimes it is ~50ms. Let me know if I am doing anything wrong in this.

```

struct timespec delay = { 0, 100*1000*1000L };  // 10 msec
int timer_return;
struct timespec requestStart;

    while(1) //Business logic runs forever
    {
        for (;;) //loop for sleep completion
        {
            printf("\n***********************Test sleep start*************************\n");
            clock_gettime(CLOCK_MONOTONIC, &requestStart);
            printf(" Before sleep time stamp is nsec = %d, sec = %d\n",requestStart.tv_nsec, requestStart.tv_sec);
            
            timer_return = nanosleep(&delay, &delay);
            if ( timer_return < 0) 
            {
                printf("Sleep interrupted by system call, Continue to sleep, Error number: %d, return value of sleep %d\n", errno, timer_return);
                if (errno == EINTR)            
                    continue;
            }
                
            else if (timer_return == 0)
            {
                clock_gettime(CLOCK_MONOTONIC, &requestStart);
                printf(" After sleep time complete, time is nsec = %d, sec = %d",requestStart.tv_nsec, requestStart.tv_sec);
                printf("\n Sleep complete, break out of loop, return value of sleep: %d\n", timer_return);
                break;
            }
        }
        printf("\n***********************Test sleep end*************************\n");

        //Business logic to be introduced here;
    }

```


Below log is for one such instance. there are logs where the sleep completes in 50ms

> ***********************Test sleep start*************************
 Before sleep time stamp is nsec = 621636654, sec = 5987
 After sleep time complete, time is nsec = 712417487, sec = 5987
 Sleep complete, break out of loop, return value of sleep: 0

***********************Test sleep end*************************

---

### Post by Vinayaka_Negalur on 2015-08-14
Hello experts,

Can some one help me and give me his expert advice/suggestion..
This is little urgent for me to achieve this..

---

