---
title: "vnc recommendations"
date: 2021-07-10
forum: General Help
---

### Post by edstevens on 2021-07-10
Two personal laptops on home network. One running Ubuntu  16.04 LTS, the other Windows 10 Pro.  For some time I have been using RealVNC to connect to the Ubuntu from the windows.  I no longer have a need to do this across the internet, just across my home network.  I would like to to remove RealVNC (and close my account) and install a vnc product that will only communicate across my home network.  Any suggestions?

---

### Post by HermanAB on 2021-07-10
Use SSH instead. It is a Swiss Army Knife and can do much more than VNC -  securely. Both Linux and Windows 10 support SSH.

---

### Post by TheFu on 2021-07-10
16.04 support ended a few months ago.  Using it is asking to be hacked.
To connect to Linux, use ssh for management or x2go if a full desktop is needed.  On the same LAN, I use normal X11 connectivity. It is fast, efficient, and doesn't bring the bloat of a full desktop when just 1 application is desired.

Steps:
1) move to a 20.04-based system
2) Load the ssh and X/Server from the Windows-store (there are how-to guides on Windows websites) [https://medium.com/javarevisited/using-wsl-2-with-x-server-linux-on-windows-a372263533c3](https://medium.com/javarevisited/using-wsl-2-with-x-server-linux-on-windows-a372263533c3) is one.
3) Use ssh -X on Windows to remote into Linux and run an application that gets presented on the Windows desktop as a Window.

Don't bother with non-secure VNC or RDP ever again.

---

### Post by edstevens on 2021-07-10
Sometimes one inadvertently puts on a set of blinders!  At my job (from which I recently retired, as an Oracle DBA) I always ran xming on my workstation, then used putty with x-11 port forwarding to connect to my Oracle Linux servers.  Of course that opened a command line session, but if I occasionally needed to launch a GUI app, it handled it just fine.  Somehow I overlooked that what I'm wanting to do on my home network is essentially the same.  The big difference is that on my Ubuntu laptop, I run the Cinnamon graphical desktop, and want that redirected to my Windows machine.  

So, I launch xming on my windows machine, then use putty to connect to the Ubuntu.  But when I try to launch a graphical desktop from that command line, I get the following:

```
ed@ed-Gazelle-00:~$ startx

/usr/lib/xorg/Xorg.wrap: Only console users are allowed to run the X server
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
Couldn't get a file descriptor referring to the console
ed@ed-Gazelle-00:~$
```

I tried googling the two key error messages, but came up with nothing that was immediately helpful.
Same result when starting from a Windows command prompt, then issuing 'ssh -X username@targetname'

Also, just my standard simple check that GUI apps are being supported, opening xclock.  From the Windows ssh window:

```
ed@ed-Gazelle-00:~$ xclock
Error: Can't open display
ed@ed-Gazelle-00:~$
```    

From the putty window, it actually opened the clock. but I was a bit surprised that I couldn't reposition it.

---

### Post by scorp123 on 2021-07-10
> **edstevens said:**
> I run the Cinnamon graphical desktop, and want that redirected to my Windows machine.  

```
ed@ed-Gazelle-00:~$ startx

```



You don't need the full "startx" stuff, if you have XMing redirection working you could also try starting the desktop session directly, without all the driver overhead and graphical mode settings and what not that "startx" tries to do as well. Your local XMing already took care of that so those parts aren't needed anyway.

So the Cinnamon session command should be something like ...
```
cinnamon-session &
```

Alternative plan and perhaps easier to use? Use something like **Teamviewer** or **AnyDesk** between your Linux and your Windows machine. They're commercial software but "free to use" ("free" as in "no costs") for private users. Just make sure you secure whichever you use, e.g. complex and long password, 2FA, only allow specific ID's to connect (e.g. your's), only allow unattended remote access by white-listed ID's (your's). 

[https://anydesk.com/]("https://anydesk.com/")
[https://www.teamviewer.com/]("https://www.teamviewer.com/")

---

### Post by ActionParsnip on 2021-07-10
What are you doing on the remote system that needs the full desktop? What do you do once you connect via VNC?

---

### Post by TheFu on 2021-07-10
Set the DISPLAY environment variable correctly inside your ssh session and run **xhost + {remote-hostname-or-IP-address}**
For Unix-to-Unix ssh, **ssh -X name-of-program** will set the DISPLAY to use the ssh-tunnel DISPLAY.
Windows makes all of this hard.

For example, I run thunderbird on a different system. Here's the command I use:
```
ssh -X  regulus "firejail thunderbird " &
```

Regulus is the remote system.  My usernames are the same on both systems, if they weren't, it would be *thefu@regulus*.
If regulus can't be found by name, then there are 2 choices - setup name resolution (DNS or /etc/hosts) or use the IP address.

Beware that X11 not over ssh is insecure.

---

### Post by edstevens on 2021-07-11
As for AnyDesk or TeamViewer, that looks like I'd just be trading one  internet-based connection service for another.  My objective is to be  completely self-contained within my home network.

As for needing to set DISPLAY, that's what x-11 port forwarding is for.   When I first started doing remote connections (quite a few years ago) I  would set DISPLAY, but once I learned about port forwarding, I've  always configured my putty connections for that and have never worried  about DISPLAY again.

With my putty session and xming I can connect and launch individual GUI  apps like xclock and VirtualBox with no issues.  But if I try to launch  an entire desktop, no joy. Following is the log of the putty session. I  normally dislike when people just dump an extensive log or trace without  doing any due diligence, ignoring obvious self-explanatory or  well-defined error messages.  But in this case I can't see anything I  can really get my hands on.  But that's probably due to working outside  of my area of expertise on this one.

```
ed@ed-Gazelle-00:~$ cinnamon-session &
[1] 31684
ed@ed-Gazelle-00:~$ cinnamon-session[31684]: WARNING: t+0.04191s: CSIdleMonitor: IDLETIME counter not found
cinnamon-session[31684]: GLib-GObject-CRITICAL: t+0.04203s: object CSIdleMonitor 0x1387440 finalized while still in-construction
cinnamon-session[31684]: GLib-GObject-CRITICAL: t+0.04205s: Custom constructor for class CSIdleMonitor returned NULL (which is invalid). Please use GInitable instead.
SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
Xlib:  extension "DPMS" missing on display "localhost:10.0".

(cinnamon-settings-daemon:31724): power-plugin-WARNING **: No idle counter

(cinnamon-settings-daemon:31724): power-plugin-WARNING **: Failed set DPMS mode: Display is not DPMS capable
=== xinerama setup Configuration ===
  Clone: false
  Output: Laptop attached to default
     status: on
     width: 1366
     height: 768
     rate: 0
     primary: true
     position: 0 0
=== Applying Configuration Configuration ===
  Clone: false
  Output: Laptop attached to default
     status: on
     width: 1366
     height: 768
     rate: 0
     primary: true
     position: 0 0

(cinnamon-settings-daemon:31724): power-plugin-WARNING **: Unable to inhibit lid switch: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Permission denied

(cinnamon-settings-daemon:31724): media-keys-plugin-WARNING **: Unable to inhibit keypresses: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Permission denied
Xlib:  extension "DPMS" missing on display "localhost:10.0".
=== xinerama setup Configuration ===
  Clone: false
  Output: Laptop attached to default
     status: on
     width: 1366
     height: 768
     rate: 0
     primary: true
     position: 0 0
=== Applying Configuration Configuration ===
  Clone: false
  Output: Laptop attached to default
     status: on
     width: 1366
     height: 768
     rate: 0
     primary: true
     position: 0 0
Xlib:  extension "DPMS" missing on display "localhost:10.0".
Xlib:  extension "DPMS" missing on display "localhost:10.0".

(cinnamon-settings-daemon:31724): color-plugin-WARNING **: failed to get edid: unable to get EDID for output
[1626025323,000,xklavier.c:xkl_engine_start_listen/] The backend does not require manual layout management - but it is provided by the application

(cinnamon-settings-daemon:31724): color-plugin-WARNING **: failed to create device: failed to obtain org.freedesktop.color-manager.create-device auth

(cinnamon-settings-daemon:31724): color-plugin-WARNING **: no xrandr-eDP1 device found: Failed to find output xrandr-eDP1

(cinnamon-settings-daemon:31724): color-plugin-WARNING **: failed to obtain org.freedesktop.color-manager.create-profile auth

(cinnamon-settings-daemon:31724): color-plugin-WARNING **: failed to obtain org.freedesktop.color-manager.create-profile auth

(cinnamon-settings-daemon:31724): color-plugin-WARNING **: failed to obtain org.freedesktop.color-manager.create-profile auth

(cinnamon-settings-daemon:31724): color-plugin-WARNING **: failed to obtain org.freedesktop.color-manager.create-profile auth

(cinnamon-settings-daemon:31724): color-plugin-WARNING **: failed to obtain org.freedesktop.color-manager.create-profile auth

(cinnamon-settings-daemon:31724): color-plugin-WARNING **: failed to obtain org.freedesktop.color-manager.create-profile auth

(cinnamon-settings-daemon:31724): color-plugin-WARNING **: failed to obtain org.freedesktop.color-manager.create-profile auth

(cinnamon-settings-daemon:31724): color-plugin-WARNING **: failed to obtain org.freedesktop.color-manager.create-profile auth
Window manager warning: Software rendering detected: llvmpipe (LLVM 6.0, 256 bits)

(process:31805): AccountsService-WARNING **: Could not get current seat: No data available
initctl: UPSTART_SESSION isn't set in the environment. Unable to locate the Upstart instance.
(uint32 2,)

(process:31882): indicator-sound-WARNING **: volume-control-pulse.vala:735: unable to get pulse unix socket: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.PulseAudio1 was not provided by any .service files
EC_generateKey_FIPS_consistancy_test: GOOD Signature Verify!

Window manager warning: Missing composite extension required for compositingEC_generateKey_FIPS_consistancy_test: GOOD Signature Verify!

EC_generateKey_FIPS_consistancy_test: GOOD Signature Verify!

EC_generateKey_FIPS_consistancy_test: GOOD Signature Verify!

EC_generateKey_FIPS_consistancy_test: GOOD Signature Verify!


(tracker-extract:31865): Tracker-WARNING **: Task 0, error: Unable to insert multiple values for subject `urn:uuid:ce414aa8-98f5-d692-30ed-9281b2acc052' and single valued property `nfo:wordCount' (old_value: '194', new value: '183')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:ce414aa8-98f5-d692-30ed-9281b2acc052> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:ce414aa8-98f5-d692-30ed-9281b2acc052> a nfo:PaginatedTextDocument ;
 nfo:pageCount "2" ;
 nfo:wordCount "183" ;
 nfo:characterCount "1138" ;
 nie:contentCreated "2016-04-02T00:41:00Z" ;
 nco:publisher [ a nco:Contact ;
 nco:fullname "ed"] ;
 nie:comment "" ;
 nie:contentLastModified "2019-12-02T15:27:46Z" ;
 nie:subject "" ;
 nie:title "" ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 1, error: Unable to insert multiple values for subject `urn:uuid:d41a69b4-29c2-09a3-33dc-ed8d11e270cb' and single valued property `nie:generator' (old_value: 'LibreOffice/5.1.6.2$Linux_X86_64 LibreOffice_project/10m0$Build-2', new value: 'LibreOffice/6.2.2.2$Linux_X86_64 LibreOffice_project/20$Build-2')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:d41a69b4-29c2-09a3-33dc-ed8d11e270cb> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:d41a69b4-29c2-09a3-33dc-ed8d11e270cb> a nfo:PaginatedTextDocument ;
 nie:contentCreated "2017-07-30T18:52:03.999649542" ;
 nie:generator "LibreOffice/6.2.2.2$Linux_X86_64 LibreOffice_project/20$Build-2" ;
 nfo:pageCount "1" ;
 nfo:wordCount "265" ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 2, error: Unable to insert multiple values for subject `urn:uuid:e68db87f-37e3-8f31-5c85-040e91f08af0' and single valued property `nie:generator' (old_value: 'LibreOffice/5.1.6.2$Linux_X86_64 LibreOffice_project/10m0$Build-2', new value: 'LibreOffice/6.2.4.2$Linux_X86_64 LibreOffice_project/20$Build-2')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:e68db87f-37e3-8f31-5c85-040e91f08af0> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:e68db87f-37e3-8f31-5c85-040e91f08af0> a nfo:PaginatedTextDocument ;
 nie:contentCreated "2018-03-17T11:15:47.399129017" ;
 nie:generator "LibreOffice/6.2.4.2$Linux_X86_64 LibreOffice_project/20$Build-2" ;
 nfo:pageCount "4" ;
 nfo:wordCount "929" ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 3, error: Unable to insert multiple values for subject `urn:uuid:48e82237-cc40-f7c8-b032-3b1161e97f0e' and single valued property `nie:generator' (old_value: 'LibreOffice/6.0.6.2$Linux_X86_64 LibreOffice_project/00m0$Build-2', new value: 'LibreOffice/6.1.2.1$Linux_X86_64 LibreOffice_project/10$Build-1')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:48e82237-cc40-f7c8-b032-3b1161e97f0e> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:48e82237-cc40-f7c8-b032-3b1161e97f0e> a nfo:PaginatedTextDocument ;
 nie:contentCreated "2018-08-20T14:50:14.548515245" ;
 nie:generator "LibreOffice/6.1.2.1$Linux_X86_64 LibreOffice_project/10$Build-1" ;
 nfo:pageCount "2" ;
 nfo:wordCount "413" ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 4, error: Unable to insert multiple values for subject `urn:uuid:ba23e6c2-d4a9-caf9-04f3-fbcb495ee178' and single valued property `nie:generator' (old_value: 'LibreOffice/6.1.2.1$Linux_X86_64 LibreOffice_project/10$Build-1', new value: 'LibreOffice/6.2.4.2$Linux_X86_64 LibreOffice_project/20$Build-2')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:ba23e6c2-d4a9-caf9-04f3-fbcb495ee178> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:ba23e6c2-d4a9-caf9-04f3-fbcb495ee178> a nfo:PaginatedTextDocument ;
 nie:contentCreated "2018-10-12T09:24:29.303029006" ;
 nie:generator "LibreOffice/6.2.4.2$Linux_X86_64 LibreOffice_project/20$Build-2" ;
 nfo:pageCount "5" ;
 nfo:wordCount "1275" ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 5, error: Unable to insert multiple values for subject `urn:uuid:d12df7f2-e723-9c82-5504-e9812ea684c5' and single valued property `nie:generator' (old_value: 'LibreOffice/6.1.2.1$Linux_X86_64 LibreOffice_project/10$Build-1', new value: 'LibreOffice/6.2.3.2$Linux_X86_64 LibreOffice_project/20$Build-2')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:d12df7f2-e723-9c82-5504-e9812ea684c5> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:d12df7f2-e723-9c82-5504-e9812ea684c5> a nfo:PaginatedTextDocument ;
 nie:contentCreated "2018-10-12T09:00:49.356821305" ;
 nie:generator "LibreOffice/6.2.3.2$Linux_X86_64 LibreOffice_project/20$Build-2" ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 6, error: Unable to insert multiple values for subject `urn:uuid:0156d9cb-5eec-3723-dce9-66168320f651' and single valued property `nfo:wordCount' (old_value: '1431', new value: '1459')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:0156d9cb-5eec-3723-dce9-66168320f651> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:0156d9cb-5eec-3723-dce9-66168320f651> a nfo:PaginatedTextDocument ;
 nie:contentCreated "2019-03-26T18:24:31.649069406" ;
 nie:generator "LibreOffice/6.1.5.2$Linux_X86_64 LibreOffice_project/10$Build-2" ;
 nfo:pageCount "4" ;
 nfo:wordCount "1459" ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 7, error: Unable to insert multiple values for subject `urn:uuid:fc26ea3c-733d-4c41-4a9d-0b3abd417f13' and single valued property `nfo:wordCount' (old_value: '41', new value: '81')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:fc26ea3c-733d-4c41-4a9d-0b3abd417f13> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:fc26ea3c-733d-4c41-4a9d-0b3abd417f13> a nfo:PaginatedTextDocument ;
 nie:contentCreated "2019-06-18T12:46:38.096565580" ;
 nie:generator "LibreOffice/6.2.4.2$Linux_X86_64 LibreOffice_project/20$Build-2" ;
 nfo:pageCount "1" ;
 nfo:wordCount "81" ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 8, error: Unable to insert multiple values for subject `urn:uuid:f7ca085a-756d-4d5c-4781-16777a53daa1' and single valued property `nfo:wordCount' (old_value: '170', new value: '230')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:f7ca085a-756d-4d5c-4781-16777a53daa1> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:f7ca085a-756d-4d5c-4781-16777a53daa1> a nfo:PaginatedTextDocument ;
 nie:contentCreated "2020-02-16T10:17:22.622897886" ;
 nie:generator "LibreOffice/6.2.4.2$Linux_X86_64 LibreOffice_project/20$Build-2" ;
 nfo:pageCount "2" ;
 nfo:wordCount "230" ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 9, error: Unable to insert multiple values for subject `urn:uuid:24b977c9-1f9a-01d2-72dc-4412ab3e4398' and single valued property `nfo:pageCount' (old_value: '3', new value: '4')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:24b977c9-1f9a-01d2-72dc-4412ab3e4398> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:24b977c9-1f9a-01d2-72dc-4412ab3e4398> a nfo:PaginatedTextDocument ;
 nfo:pageCount 4 ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 10, error: Unable to insert multiple values for subject `urn:uuid:45c5c6f7-6744-6890-68c5-b6013b909eaa' and single valued property `nie:plainTextContent' (old_value: 'Account Change Date Desktop  Dorothy 04/23/20 Desktop  Ed 04/23/20 Bitwarden  Dorothy 04/23/20 Bitwarden  Ed 04/23/20 Facebook  Dorothy 04/23/20 Facebook  Ed 04/24/20 VNC Email  Dorothy Email  Ed ', new value: 'Account Change Date Desktop  Dorothy 04/23/20 Desktop  Ed 04/23/20 Bitwarden  Dorothy 04/23/20 Bitwarden  Ed 04/23/20 Facebook  Dorothy 04/23/20 Facebook  Ed 04/24/20 VNC Email  Dorothy 04/25/20 Email  Ed ')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:45c5c6f7-6744-6890-68c5-b6013b909eaa> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:45c5c6f7-6744-6890-68c5-b6013b909eaa> a nfo:PaginatedTextDocument ;
 nie:contentCreated "2020-04-24T09:45:59.527190739" ;
 nie:generator "LibreOffice/6.2.4.2$Linux_X86_64 LibreOffice_project/20$Build-2" ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 11, error: Unable to insert multiple values for subject `urn:uuid:0597ec65-13a0-8c58-a570-89d12b65ca7b' and single valued property `nfo:pageCount' (old_value: '6', new value: '9')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:0597ec65-13a0-8c58-a570-89d12b65ca7b> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:0597ec65-13a0-8c58-a570-89d12b65ca7b> a nfo:PaginatedTextDocument ;
 nie:contentCreated "2020-04-26T08:39:02.175295038" ;
 nie:generator "LibreOffice/6.2.4.2$Linux_X86_64 LibreOffice_project/20$Build-2" ;
 nfo:pageCount "9" ;
 nfo:wordCount "2197" ;
 


(tracker-extract:31865): Tracker-WARNING **: Task 12, error: Unable to insert multiple values for subject `urn:uuid:95e6b55b-a7ca-900e-1281-819c6e50ce16' and single valued property `nfo:pageCount' (old_value: '5', new value: '4')
Sparql was:
INSERT {
GRAPH <urn:uuid:472ed0cc-40ff-4e37-9c0c-062d78656540> {
<urn:uuid:95e6b55b-a7ca-900e-1281-819c6e50ce16> nie:dataSource <http://www.tracker-project.org/ontologies/tracker#extractor-data-source> .
<urn:uuid:95e6b55b-a7ca-900e-1281-819c6e50ce16> a nfo:PaginatedTextDocument ;
 nie:contentCreated "2020-05-19T16:42:27.430092197" ;
 nie:generator "LibreOffice/6.2.4.2$Linux_X86_64 LibreOffice_project/20$Build-2" ;
 nfo:pageCount "4" ;
 nfo:wordCount "722" ;
 


(process:31882): AccountsService-WARNING **: Could not get current seat: No data available

** (polkit-gnome-authentication-agent-1:31889): WARNING **: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Cannot register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
blueman-applet version 2.0.4 starting
There is an instance already running

(nm-applet:31907): nm-applet-WARNING **: GDBus.Error:org.freedesktop.NetworkManager.AgentManager.PermissionDenied: An agent with this ID is already registered for this user.

** (nemo:31890): WARNING **: Can not determine workarea, guessing at layout
Jul 11 12:42:21.799 [VIA INFO Logging():core/Logging.cpp:23] VIA Logging has been initialized

Jul 11 12:42:21.799 [VIA INFO ViaCipher():core/ViaCipher.cpp:7] VIA cipher has been created

Jul 11 12:42:21.799 [VIA INFO ViaApplication():core/ViaApplication.cpp:59] VIA application version: 3.0.0.82618

Jul 11 12:42:21.799 [VIA INFO ViaApplication():core/ViaApplication.cpp:60] VIA command line arguments: via-ui

Jul 11 12:42:21.804 [VIA INFO init():core/ViaApplication.cpp:203] VIA application initialization...

Jul 11 12:42:21.888 [VIA INFO processOptions():core/ViaApplication.cpp:388] Processing VIA options...

Jul 11 12:42:21.889 [VIA INFO createIpcServer():core/IpcServer.cpp:134] Creating UI IPC server (via-ipc-ui)...

Jul 11 12:42:21.889 [VIA INFO createIpcServer():core/IpcServer.cpp:146] UI IPC server is already running

Jul 11 12:42:21.889 [VIA INFO sendIpcEvent():core/IpcServer.cpp:57] IPC event sender: EVENT_UI_TO_UI_ANOTHER_INSTANCE_LAUNCHED -> via-ipc-ui

Jul 11 12:42:21.903 [VIA ERROR CRYPTO_LIB_deinit():crypto_lib.c:356] Crypto library not initialized

Jul 11 12:42:21.904 [VIA INFO ~ViaCipher():core/ViaCipher.cpp:13] VIA cipher destroyed

Jul 11 12:42:21.904 [VIA INFO ~Logging():core/Logging.cpp:28] VIA Logging released


** (zeitgeist-datahub:32096): WARNING **: kde-recent-document-provider.vala:174: Couldn't find actor for 'krecipes'.

** (zeitgeist-datahub:32096): WARNING **: kde-recent-document-provider.vala:174: Couldn't find actor for 'krecipes'.
Xlib:  extension "DPMS" missing on display "localhost:10.0".

(gnome-software:31850): GsPlugin-WARNING **: could not lookup cached macaroon: Error calling StartServiceByName for org.freedesktop.secrets: Timeout was reached
/usr/share/system-config-printer/applet.py:45: PyGIWarning: Notify was imported without specifying a version first. Use gi.require_version('Notify', '0.7') before import to ensure that the right version gets loaded.
  from gi.repository import Notify

```

At this point it did open a full, blank screen, with no borders and no controls.  Alt-Tab did take me out of it to the other windows that were open on the Windows desktop.

---

### Post by scorp123 on 2021-07-11
> **edstevens said:**
> As for AnyDesk or TeamViewer, that looks like I'd just be trading one  internet-based connection service for another.  My objective is to be  completely self-contained within my home network

Ok then, let's try the following.

**_On your Linux system:_**

Execute the following commands please:

```

sudo apt install x2goserver x2goserver-xsession

```

This will install the **X2go** server.


**_On your Windows system:_**

Download and install this program:
[https://code.x2go.org/releases/X2GoClient_latest_mswin32-setup.exe]("https://code.x2go.org/releases/X2GoClient_latest_mswin32-setup.exe")

When it's installed and available (e.g. via the "Start" menu) fire it up and enter the details for your host, e.g. you'd go into the application's menu and go:
```
Session > New Session... (Ctrl+N)
```

The window you should be getting will look like this:  (link to screenshot)
[https://i2.paste.pics/7192927f4468726973afc5d532138bab.png]("https://i2.paste.pics/7192927f4468726973afc5d532138bab.png")

Please fill out / correct the areas I marked red on the screenshot.

On the *"Connection"* tab, change the speed setting to **"LAN"** ...
On the *"Input/Output"* tab, change the resolution, e.g. to **"Fullscreen"** or **"Maximum available"**

Make sure you save these settings as your new session.

And now try it out. If everything worked correctly you should now be seeing your remote Cinnamon desktop on your Windows PC. Mission accomplished?

---

### Post by scorp123 on 2021-07-11
And if you are already logged in remotely (e.g. you're already logged in and Cinnamon is running) and you'd like to get ***that*** exact session onto your Windows client, change the session type to:

**"X2go/X11 Desktop Sharing"**

If everything is working correctly then you should be getting your remote already running Cinnamon session that you left on your Linux machine now showing on your Windows PC. Works tip top for me and my **Budgie** desktop, so I don't see why it wouln't work for you...

---

### Post by edstevens on 2021-07-12
Trying the x2goserver route:

```
ed@ed-Gazelle-00:~$ sudo apt install x2goserver x2goserver-xsession
[sudo] password for ed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package x2goserver
E: Unable to locate package x2goserver-xsession
ed@ed-Gazelle-00:~$ 
```

Additional preliminary steps, detailed at [https://wiki.x2go.org/doku.php/doc:installation:x2goserver](https://wiki.x2go.org/doku.php/doc:installation:x2goserver), seem to have worked, albeit with some warnings about 'older packages/libraries'.

---

### Post by edstevens on 2021-07-12
OK, almost there.  Installed x2go server on the linux box, and client on the windows.  Got the connection, and _most_ of the desktop.  As you may know, the Cinnamon desktop has the same 'look and feel' as Windows, which is why I chose it.  When it comes up in x2go, it is lacking the 'status' bar, which has the Menu button, as well as some shortcuts, and tabs for any running, forground process.  Actually, even bottom-most icon on the desktop is cut  a bit short, so it appears that the bottom most part of the display is cut off.  This happens with any of the three possible setting for input/output -- Full Screen, Maximum, or Custom with the default width/height of 1366 x 728.

I also tried the Unity and Gnome desktops, which I have used some in the past, but they only came up with a black screen and no content.

---

### Post by TheFu on 2021-07-12
For GUI stuff, 
[LIST]
[*]On the LAN, I use ssh -X forwarding.
[*]Over the internet, I use x2go. It works well from 5 continents. For a few years, I used it from a Win7 desktop, before I stopped using Windows except when no other method was available.
[/LIST]

x2go will probably die when Wayland completely takes over the Linux desktop.  x2go is built from an X/Server version from 2009, before NoMachine forked into the proprietary software world.

A few tricks for using x2go.  Assuming you've added the x2go PPA to your APT setup (x2go-ubuntu-stable-focal.list)
[LIST]
[*]set the connection speed to be 1-less than the actual speed.
[*]set the image compression to be 4kb-png
[*]disable printing and desktop shares throgh the x2go-client GUI
[*]setup ssh-keys using the x2go included ssh-keygen program. The Putty program is not compatible.
[*]on Windows, install the full font package from the x2go website. Windows doesn't include most standard Unix X/Client fonts, so those are necessary.
[/LIST]

ssh-keygen on Windows using the x2go version works exactly the same as ssh-keygen on Linux does.  The RSA-based keys shouldn't be used anymore. Use ed25519 keys for greater security:
```
ssh-keygen -t ed25519
```
[https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278](https://ubuntuforums.org/showthread.php?t=2443909&p=13959278#post13959278) has more about ssh keys and securing ssh connections.

---

### Post by edstevens on 2021-07-12
TheFu -  please read my previous replies.  I actually would have preferred ssh with x-forwarding.  My setup there was putty and xmin.  Please see extensive log I posted of where this failed.

---

### Post by TheFu on 2021-07-12
> **edstevens said:**
> TheFu -  please read my previous replies.  I actually would have preferred ssh with x-forwarding.  My setup there was putty and xmin.  Please see extensive log I posted of where this failed.

I saw that, but since your client is Windows, I had nothing to offer.  Last time I used Windows with an X/Server must have been 2001-ish.  In my world, it was always easier to run a tiny Linux VM with a real X/Server and use standard ssh + X/Server capabilities.  TinyCore with X/Windows is 20MB.  I wouldn't bother with whatever MSFT is trying to accomplish with their Linux dabbles, but that's just me.

---

### Post by edstevens on 2021-11-11
Please accept my sincere apology for abandoning this thread without final resolution.  No excuses.  

To reiterate my latest status:

Installed x2go server on the linux box, and client on the windows.  Got  the connection, and _most_ of the desktop.  As you may know, the  Cinnamon desktop has the same 'look and feel' as Windows, which is why I  chose it.  When it comes up in x2go, it is lacking the 'status' bar,  which has the Menu button, as well as some shortcuts, and tabs for any  running, forground process.  Actually, even bottom-most icon on the  desktop is cut  a bit short, so it appears that the bottom most part of  the display is cut off.  This happens with any of the three possible  setting for input/output -- Full Screen, Maximum, or Custom with the  default width/height of 1366 x 728.

I also tried the Unity and Gnome desktops, which I have used some in the  past, but they only came up with a black screen and no content.

---

