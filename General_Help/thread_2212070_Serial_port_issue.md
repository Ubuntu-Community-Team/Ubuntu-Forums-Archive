---
title: "Serial port issue"
date: 2014-03-19
forum: General Help
---

### Post by yevhen2 on 2014-03-19
[FONT=arial]Hi, All[/FONT][FONT=arial]
[/FONT]
[FONT=arial][FONT=arial, sans-serif]I am using [/FONT][FONT=sans-serif]Ubuntu 12.04 

[/FONT][/FONT]
[FONT=arial][FONT=sans-serif]I would like to work with serial port(ttymxc2). [/FONT][/FONT]
[FONT=arial][FONT=sans-serif]I checked, if it works by typing following commands:[/FONT][/FONT]
[FONT=arial][FONT=sans-serif]
[/FONT][/FONT]
[FONT=arial][FONT=sans-serif]root~$ stty -F /dev/ttymxc2 cs8 -parenb -cstopb 115200    [COLOR=#ff0000]# works, port init[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=sans-serif]root~$ cat /dev/ttymxc2                                                  [COLOR=#ff0000]# works, can see messages from my PC[/COLOR][/FONT]
[/FONT]
[FONT=arial][FONT=sans-serif]root~$ echo Hello world > /dev/ttymxc2                            [COLOR=#ff0000]#doesn`t work, can`t see messages on my PC[/COLOR][/FONT][FONT=sans-serif]
[/FONT][/FONT]
[FONT=arial][FONT=sans-serif]
[/FONT][/FONT]
[FONT=arial][FONT=sans-serif]After tese actions I have tried the other port - ttymxc0, and it works.[/FONT][/FONT]
[FONT=arial][FONT=sans-serif]root~$ stty -F /dev/ttymxc0 cs8 -parenb -cstopb 115200    [/FONT][COLOR=#FF0000][FONT=sans-serif]# works, port init[/FONT][/COLOR]
[FONT=sans-serif]root~$ cat /dev/ttymxc0                                                  [/FONT][FONT=sans-serif] [/FONT][COLOR=#ff0000][FONT=sans-serif]# works, can see messages from my PC, mixed with debug information[/FONT][/COLOR]

[FONT=sans-serif]root~$ echo Hello world > /dev/ttymxc0                             [COLOR=#ff0000]# works, can see messages on my PC[/COLOR][/FONT]
[/FONT]
[FONT=arial][FONT=sans-serif][COLOR=#ff0000]
[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=sans-serif][COLOR=#000000]Is there something I missing? Is ttymxc2 somehow unique? Program I wrote on C language have the same behavior - read function works properly with both mxc0, mxc2, but write function works only with mxc0. However write function doesn`t return -1, it returns a number of sent chars, as expected.[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=sans-serif][COLOR=#000000]
[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=sans-serif][COLOR=#000000]Thank you in advance,[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=sans-serif][COLOR=#000000]Yevhen[/COLOR][/FONT][/FONT]

---

