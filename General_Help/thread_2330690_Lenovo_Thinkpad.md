---
title: "Lenovo Thinkpad"
date: 2016-07-13
forum: General Help
---

### Post by Richardo_Petri on 2016-07-13
Hey!

I'm familiar with Unix based systems and have installed Ubuntu on a laptop that I have a problem with.

For some reason after almost precisely 30 min (something like 26 min) the laptop just dies.

I've tried almost everything.

Updated windows, ran in safe mode, reinstalled windows.

Booted onto Knoppix-live-cd...

Memtest is OK 
HDD test is OK
Prime 95 no problems (unless I wait the 30 min)

Temps are OK.

I have updated BIOS, then reverted it then updated it again.

I've changed the system memory and the HDD.

Now I've installed ubuntu 16 and trying to use Apport to generate a crash rapport but after the crash i could not find it in /var/crash.

Where do I find the Crash rapport? Or how do I generate one.

And what else is there to do? What is my next step here.


Ohh I have a rapport from windows but I can not make sense of it.

these are the last two entriesd in windows event viewer before it crasches.
> [COLOR=#282828][FONT=Arial]Log Name: Application[/FONT][/COLOR][COLOR=#282828][FONT=Arial]Source: Microsoft-Windows-CAPI2
Date: 2016-01-28 22:57:48
Event ID: 513
Task Category: None
Level: Error
Keywords: Classic
User: N/A
Computer: Löfgren-PC
Description:
Cryptographic Services failed while processing the OnIdentity() call in the System Writer Object.[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]Details:
AddLegacyDriverFiles: Unable to back up image of binary ksqcraes.[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]System Error:
The system cannot find the file specified.
.
Event Xml:
<Event xmlns="[http://schemas.microsoft.com/win/2004/08/events/event](http://schemas.microsoft.com/win/2004/08/events/event)">
<System>
<Provider Name="Microsoft-Windows-CAPI2" Guid="{5bbca4a8-b209-48dc-a8c7-b23d3e5216fb}" EventSourceName="Microsoft-Windows-CAPI2" />
<EventID Qualifiers="0">513</EventID>
<Version>0</Version>
<Level>2</Level>
<Task>0</Task>
<Opcode>0</Opcode>
<Keywords>0x8080000000000000</Keywords>
<TimeCreated SystemTime="2016-01-28T21:57:48.201040700Z" />
<EventRecordID>626</EventRecordID>
<Correlation />
<Execution ProcessID="1520" ThreadID="1576" />
<Channel>Application</Channel>
<Computer>Löfgren-PC</Computer>
<Security />
</System>
<EventData>
<Data>[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]Details:
AddLegacyDriverFiles: Unable to back up image of binary ksqcraes.[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]System Error:
The system cannot find the file specified.
</Data>
</EventData>
[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]</Event>[/FONT][/COLOR]


> [COLOR=#282828][FONT=Arial]<Event xmlns="[/FONT][/COLOR][http://schemas.microsoft.com/win/2004/08/events/event](http://schemas.microsoft.com/win/2004/08/events/event)[COLOR=#282828][FONT=Arial]">[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]- <System>[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Provider Name="Microsoft-Windows-WMI" Guid="{1edeee53-0afe-4609-b846-d8c0b2075b1f}" EventSourceName="WinMgmt" /> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<EventID Qualifiers="49152">10</EventID> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Version>0</Version> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Level>2</Level> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Task>0</Task> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Opcode>0</Opcode> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Keywords>0x80000000000000</Keywords> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<TimeCreated SystemTime="2016-01-28T21:59:41.000000000Z" /> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<EventRecordID>633</EventRecordID> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Correlation /> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Execution ProcessID="0" ThreadID="0" /> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Channel>Application</Channel> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Computer>Löfgren-PC</Computer> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Security /> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]</System>[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]- <EventData>[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Data>//./root/CIMV2</Data> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Data>SELECT * FROM __InstanceModificationEvent WITHIN 60 WHERE TargetInstance ISA "Win32_Processor" AND TargetInstance.LoadPercentage > 99</Data> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]<Data>0x80041003</Data> [/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]</EventData>[/FONT][/COLOR]
[COLOR=#282828][FONT=Arial]</Event>[/FONT][/COLOR]


Thankfull for help.

---

### Post by Topsiho on 2016-07-14
Seems to me that the computer (processor?) gets too hot to function properly, after some time.
Maybe it's dirty inside? Can you clean (blow with pressed air) the ventilator? Use a laptop cooler (just to see if that makes a difference)?

Good luck,

Topsiho

---

### Post by kurt18947 on 2016-07-15
What's going to make this difficult I think is the "exactly 30 minutes" part. If it were a temperature issue as seems most likely, a machine running demanding software should shut down at shorter intervals than a machine just idling. That doesn't seem to be the case here if I'm reading correctly.

---

### Post by Topsiho on 2016-07-15
I agree. OP also says that temps are OK. 

But as it seems to be a problem in Ubuntu and in Windows, I can only guess it is hardware related.
After running some time components in the computer get hot, and might not work anymore. Probably some component gets hotter and hotter, independent of the workload.

If it is on the motherboard I guess the laptop is done for. I guess it is an old laptop, as it says a "Win32_Processor" somewhere.

Cleaning the inside of the laptop still might be tried.

Topsiho

---

