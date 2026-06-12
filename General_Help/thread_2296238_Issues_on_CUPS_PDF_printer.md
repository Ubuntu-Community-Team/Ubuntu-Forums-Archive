---
title: "Issues on CUPS PDF printer"
date: 2015-09-24
forum: General Help
---

### Post by Arno_Anderson on 2015-09-24
Hi!

I've created a Cups Server on Ubuntu and i'm trying to print from parametric monitor to PDF, but the information is not sent.
Some observations:

The parametric monitor uses Webmin Interface to add printer, only using IP address and Printer Name (no port, no http:, ipp...)

/var/log/cups: no data

Tcpdump log:
[COLOR=#333333][FONT=Helvetica Neue]19:16:48.438306 IP 192.168.2.20.50612 > 192.168.2.2.631: Flags [S], seq 3376652811, win 5840, options [mss 1460,sackOK,TS val 1136624 ecr 0,nop,wscale 5], length 0[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]19:16:48.439299 IP 192.168.2.20.50612 > 192.168.2.2.631: Flags [.], ack 4047344376, win 183, options [nop,nop,TS val 1136625 ecr 271325], length 0[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]19:16:48.442900 IP 192.168.2.20.50612 > 192.168.2.2.631: Flags [P.], seq 0:136, ack 1, win 183, options [nop,nop,TS val 1136628 ecr 271325], length 136[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]19:16:48.459695 IP 192.168.2.20.50612 > 192.168.2.2.631: Flags [P.], seq 136:509, ack 1, win 183, options [nop,nop,TS val 1136645 ecr 271326], length 373[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]19:16:48.556275 IP 192.168.2.20.50612 > 192.168.2.2.631: Flags [.], ack 26, win 183, options [nop,nop,TS val 1136728 ecr 271351], length 0[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]19:16:48.560213 IP 192.168.2.20.50612 > 192.168.2.2.631: Flags [.], ack 233, win 216, options [nop,nop,TS val 1136742 ecr 271354], length 0[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]19:16:48.560237 IP 192.168.2.20.50612 > 192.168.2.2.631: Flags [.], ack 363, win 250, options [nop,nop,TS val 1136742 ecr 271355], length 0[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]19:16:48.560243 IP 192.168.2.20.50612 > 192.168.2.2.631: Flags [F.], seq 509, ack 363, win 250, options [nop,nop,TS val 1136746 ecr 271355], length 0[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]19:16:48.682306 IP 192.168.2.20.50612 > 192.168.2.2.631: Flags [.], ack 364, win 250, options [nop,nop,TS val 1136752 ecr 271357], length 0

Thanks![/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-09-24
I don't know what a "parametric monitor" is, but does it have a browser you can open to localhost:631?  Then you can talk directly to CUPS rather than using something less effective like Webmin.

---

### Post by Arno_Anderson on 2015-09-24
Hi Seiji

[COLOR=#333333][FONT=sans-serif]Parametric Monitor describes the design of a wearable multiparametric physiological signal monitor, a continuously running internetworking system for monitoring multiple physiological parameters of patients.
I can't open the "full" Webmin interface, only to add the printer.



[/FONT][/COLOR]

---

### Post by ian-weisser on 2015-09-24
There are two ways to print to PDF using CUPS. Which are you using?
The default setting in Ubuntu is to generate the PDF using a non-printer filter.
The older, probably-better-for-you way is to set up a (pseudo) printer using the printer-driver-cups-pdf package.

---

### Post by Arno_Anderson on 2015-09-24
I used [COLOR=#000000]printer-driver-cups-pdf package.

But there is no response from CUPS (logs, etc) when I send print command from the parametric monitor
Other "normal" computers normally print.

Thanks.[/COLOR]

---

### Post by ian-weisser on 2015-09-24
It seems like the CUPS server is not receiving the job, since there is no log record.

Does your parametric monitor print to other printers on the same server?
Does your parametric monitor have any other network-related issues? Can it, for example, ping the CUPS server host?
Can other machines on the same network print-to-PDF on that CUPS server?

---

### Post by Arno_Anderson on 2015-09-24
[COLOR=#000000]Does your parametric monitor print to other printers on the same server?
A: Only usb or network PCL5 compatible [/COLOR][COLOR=#000000]printers.[/COLOR][COLOR=#000000]

[/COLOR][COLOR=#000000]Does your parametric monitor have any other network-related issues? Can it, for example, ping the CUPS server host?
[/COLOR][COLOR=#000000]A: Yes.
When I send print test page from monitor, tcdump shows:
[/COLOR][COLOR=#333333][FONT=Helvetica Neue]19:16:48.438306 IP 192.168.2.20.50612 > 192.168.2.2.631: Flags [S], seq 3376652811, win 5840, options [mss 1460,sackOK,TS val 1136624 ecr 0,nop,wscale 5], length 0

[/FONT][/COLOR][COLOR=#000000]Can other machines on the same network print-to-PDF on that CUPS server?[/COLOR][COLOR=#000000]
A: Yes, works fine.

[/COLOR]
Obs:

About printing, tech support manual says:

[COLOR=#000000]Outbound Connections:[/COLOR]
[COLOR=#000000]Destination Device: Printer[/COLOR]
[COLOR=#000000]Protocol: TCP[/COLOR]
[COLOR=#000000]Destination Port: 631[/COLOR]


[COLOR=#000000]Monitor:[/COLOR]
[http://www3.gehealthcare.com/en/products/categories/patient_monitoring/patient_monitors/carescape_monitor_b650](http://www3.gehealthcare.com/en/products/categories/patient_monitoring/patient_monitors/carescape_monitor_b650) (OS Linux)
[COLOR=#000000]
Thanks!

[/COLOR]

---

