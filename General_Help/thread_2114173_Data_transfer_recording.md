---
title: "Data transfer recording?"
date: 2013-02-09
forum: General Help
---

### Post by t0p on 2013-02-09
I use a cellphone to connect my laptop to the internet.  My cellphone service provider allows me a limit of I think 1 GB of data transfer per month; after I've used that allowance the provider starts shaping my connection (eg no large file uploads or downloads or video streaming at certain times) until the next month begins.

I want my data usage to be recorded and maybe put into a spreadsheet so I can keep track of data transfer.  Unfortunately I don't know how to do this.

Can anyone point me in the right direction?  I have googled this, but the results have been a bit over my head - me and networking have never had a close relationship.

Cheers!

---

### Post by Cheesemill on 2013-02-09
The application vnstat will keep track of any data transferred through your network connections and can be used to display this information in various ways....

```
rob@arch:~$ vnstat -d

 eth0  /  daily

         day         rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
      01/30/13     28.60 MiB |  486.42 MiB |  515.02 MiB |   48.83 kbit/s
      01/31/13     23.92 GiB |    3.76 GiB |   27.68 GiB |    2.69 Mbit/s
      02/01/13      4.92 GiB |  796.72 MiB |    5.70 GiB |  553.21 kbit/s
      02/02/13      4.02 GiB |  931.10 MiB |    4.93 GiB |  479.03 kbit/s
      02/03/13      4.34 GiB |   68.21 MiB |    4.41 GiB |  428.15 kbit/s
      02/04/13    813.93 MiB |   32.83 MiB |  846.76 MiB |   80.29 kbit/s
      02/05/13     45.86 GiB |    3.69 GiB |   49.55 GiB |    4.81 Mbit/s
      02/06/13     30.97 GiB |    4.23 GiB |   35.20 GiB |    3.42 Mbit/s
      02/07/13     66.87 GiB |    4.68 GiB |   71.55 GiB |    6.95 Mbit/s
      02/08/13     84.54 GiB |    5.35 GiB |   89.89 GiB |    8.73 Mbit/s
      02/09/13     33.63 GiB |    2.23 GiB |   35.86 GiB |    5.80 Mbit/s
     ------------------------+-------------+-------------+---------------
     estimated     56.05 GiB |    3.72 GiB |   59.77 GiB |
rob@arch:~$ 
rob@arch:~$ 
rob@arch:~$ 
rob@arch:~$ vnstat -m

 eth0  /  monthly

       month        rx      |     tx      |    total    |   avg. rate
    ------------------------+-------------+-------------+---------------
      Jan '13     23.95 GiB |    4.24 GiB |   28.19 GiB |   88.28 kbit/s
      Feb '13    275.95 GiB |   21.97 GiB |  297.92 GiB |    3.36 Mbit/s
    ------------------------+-------------+-------------+---------------
    estimated    898.45 GiB |   71.53 GiB |  969.98 GiB |
rob@arch:~$ 
```

---

### Post by t0p on 2013-02-09
Thanks, I'll try that out.

---

