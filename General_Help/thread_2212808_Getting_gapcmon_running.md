---
title: "Getting gapcmon running"
date: 2014-03-23
forum: General Help
---

### Post by Peter Bell on 2014-03-23
For several years I've been running apcupsd on a Slackware server, with my Ubuntu desktop also using apcupsd, slaved from the server, via a network connection.

I have always used gapcmon to monitor the status of the UPS, but sometime, about 5 months ago, gapcmon stopped working.  Two things happened around that time - I had a corrupt root partition, and had to reinstall from scratch (thank goodness I have a separate User partition!).  Second thing was the upgrade to Saucy.  I'm not sure which of these caused gapcmon to stop working.

The symptoms are that gapcmon appears to be running - it shows up in a ps list:
```
peter@desktop:~$ ps -eaF | grep gap
peter    13627  1830  0 154696 10944  3 19:58 ?        00:00:00 gapcmon
peter    13654 12905  0  3412   956   3 20:01 pts/6    00:00:00 grep --color=auto gap

```

but nothing else happens.

I can find no entry in any logfile to suggest that there is any error reported.  Googling has shown that there have been problems with gapcmon not displaying icons.  However, I'm not sure tyhat this is my problem - I cannot find any space on the task bar/icon bar which leads to a response from gapcmon.

I have attempted several 'remedies':
o I have used Software Center to reinstall.
o I have used Synaptic to 'competely' remove and reinstall
o I have set up symbolic links to the icon files
o I have rebuilt gapcmon from latest sources (with some difficulty because of an undefined reference to 'XFlush')
o I have tried using Alien to convert an rpm to deb

None of these have resulted in a 'working' gapcmon.  I'm at a loss to know what else to try.

Does anyone have 'gapcmon' working in Saucy?
Can anyone suggest what more I can do to track down and/or fix this problem?  It appears that gapcmon sources have not been changed for some time, so I'm presuming that this problem (and the XFlush issue) are the result of underlying changes in libraries.

The only further course of action I can think of is to start building from sources with debug statements.
I gather that there is an interactive debugger available (gdb) - perhaps I have to familiarise myself with that ... but my professional background is DEC RSX-11 and VAX/Alpha VMS and FORTRAN/MACRO (showing my age here!), so I fear that I may be on a steep learning curve with this.

---

