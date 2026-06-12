---
title: "Two machines difeerent versions Ubuntu. One getting Signal 11 - Segment Violation."
date: 2020-12-26
forum: General Help
---

### Post by jay-eich on 2020-12-26
[TABLE="width: 0"]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
Greetings and Hello!!
  (( Happy Boxing Day!))

Is anyone else seeing this problem? Any insights?

I am running BOINC and World Community Grid on two machines. One is getting signal 11. The other is not.

The Work Units  with errors are only "Microbiome Immunity Project".
Other projects do not get signal 11.
The error is inconsistent.
Today, 15 Work Units (on the machine withh errors) completd without error and were validated.
And 24 exited with error.

I added debug to the WU output and checked the syslog. Nothing Jumped out at me.

The Error Message
---------------------
          Result Name: MIP1_ 00327515_ 1626_ 0-- 
            [TABLE="class: pre-foundation-table"]
[TR]
[/TR]
[TR]
[/TR]
[/TABLE]
<core_client_version>7.16.11</core_client_version>
<![CDATA[
<message>
process got signal 11</message>

        *The data goes on with initializtion OK and starting work....*




Machine with no errors.
--------------------------
Ubuntu 20.04.1 LTS with updates
Package boinc: 7.16.6+dfsg-1
Intel Core i7-3770 CPU
7.5 GiB of memory



Machine with errors
----------------------
Ubuntu 20.10
Package boinc:   7.16.15+dfsg.is.7.16.11+dfsg-1
 AMD FX(tm)-8150 Eight-Core Processor
11.6 GiB memory


----------------------------

Thanks in advance!!

Jay

PS, I have rebooted several times.

---

