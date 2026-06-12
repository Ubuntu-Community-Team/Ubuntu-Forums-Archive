---
title: "I cannot get squid to cache"
date: 2006-08-23
forum: General Help
---

### Post by CameronCalver on 2006-08-23
Hello i set up squid with many threads but i still cannot get squid to cache or check if it is caching what part of the thread would u like to me post to check on this
i did 
```
sudo tail -F /var/log/squid/store.log
``` and went on a random site and it looks like it is caching becuase of this
```
cameron@ubuntu:~$ sudo tail -F /var/log/squid/store.log
1156318658.754 RELEASE -1 FFFFFFFF ECC60FDCCA6248E23493A0335115C6B0  200 1156318 623 1137855990        -1 text/html 25651/2591 GET http://www.theweirdsite.com/
1156318662.522 SWAPOUT 00 000002FD B1DCC6A82FEAE0DAFACF1DE3D37F415D  200 1156318 623 1137855990        -1 text/html 25651/25651 GET http://www.theweirdsite.com/
1156318663.203 SWAPOUT 00 000002FE 9DBE9F93E7A51A3483C18D7EC2D07CA1  200 1156318 628 972738757        -1 image/gif 805/805 GET http://www.theweirdsite.com/makeus homepage.gif
1156318664.266 SWAPOUT 00 000002FF A4D32DD98D1B1428CAC8BADF44D3B1FD  200 1156318 628 941994032        -1 image/gif 6846/6846 GET http://www.theweirdsite.com/weir dbutton5.gif
1156318664.899 RELEASE -1 FFFFFFFF 561B0A211976A6052258095F51968B84  200 1156318 628        -1        -1 text/html 4994/4994 GET http://rcm.amazon.com/e/cm?
1156318665.619 SWAPOUT 00 00000300 E0AD9DF6486EEEA22E18CD80D3618181  200 1156318 630 1147164923        -1 image/gif 6464/6464 GET http://www.theweirdsite.com/fac t.gif
1156318665.664 SWAPOUT 00 00000301 7BA2EF6925EF7A06D80734C8F56C526D  200 1156318 630 993371091        -1 image/gif 2689/2689 GET http://www.theweirdsite.com/Inst ant-on.gif
1156318665.706 SWAPOUT 00 00000302 0E33B30F39DE2369ED2EDCAD3B80819C  200 1156318 631 945532338        -1 image/x-icon 318/318 GET http://www.theweirdsite.com/fav icon.ico
1156318678.000 RELEASE -1 FFFFFFFF 2DE05D75BB8A1E648011F4C4C32BB522  304 1156318 642        -1        -1 text/html 0/0 GET http://www.google.com.au/intl/en/nav_n ext.gif
1156318678.060 RELEASE -1 FFFFFFFF 120C0A5D02BFB48F0F78C130F214A244  304 1156318 643        -1        -1 text/html 0/0 GET http://www.google.com.au/images/firefo x_toolbar.gif
1156318782.903 RELEASE -1 FFFFFFFF 532793A6E2406E9F06CC4A56D7599764  200 1156318743        -1 1156318743 text/html -1/46228 GET http://www.ubuntuforums.org/editpost.php?
```
and here is another log
```
cameron@ubuntu:~$ sudo tail -F /var/log/squid/cache.log
2006/08/23 17:34:56|         0 Objects expired.
2006/08/23 17:34:56|         0 Objects cancelled.
2006/08/23 17:34:56|         0 Duplicate URLs purged.
2006/08/23 17:34:56|         0 Swapfile clashes avoided.
2006/08/23 17:34:56|   Took 0.3 seconds (2585.6 objects/sec).
2006/08/23 17:34:56| Beginning Validation Procedure
2006/08/23 17:34:56|   Completed Validation Procedure
2006/08/23 17:34:56|   Validated 757 Entries
2006/08/23 17:34:56|   store_swap_size = 7168k
2006/08/23 17:34:56| storeLateRelease: released 0 objects

```
so if it is caching were to and wat file does it store as

---

