---
title: "aMule crash"
date: 2007-12-17
forum: General Help
---

### Post by Thiago Cesar Vieira on 2007-12-17
Hi friends!

My aMule 2.13 is crashing after I click the button to update servers list. The link in Serverlist is default, I didn't changed:
[http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met](http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met)

When I run in console I can see bug messages:
[I]--------------------------------------------------------------------------------
A fatal error has occurred and aMule has crashed.
Please assist us in fixing this problem by posting the backtrace below in our
'aMule Crashes' forum and include as much information as possible regarding the
circumstances of this crash. The forum is located here:
    [http://forum.amule.org/board.php?boardid=67](http://forum.amule.org/board.php?boardid=67)
If possible, please try to generate a real backtrace of this crash:
    [http://www.amule.org/wiki/index.php/Backtraces](http://www.amule.org/wiki/index.php/Backtraces)

----------------------------=| BACKTRACE FOLLOWS: |=----------------------------
Current version is: aMule 2.1.3 using wxGTK2 v2.8.4 (Unicoded)
Running on: Linux 2.6.22-14-generic x86_64


** (amule:6869): CRITICAL **: clearlooks_style_draw_box_gap: assertion `height >= -1' failed
[2] wxThreadHelperThread::~wxThreadHelperThread() in amule [0x445575]
[3] wxFatalSignalHandler in /usr/lib/libwx_baseu-2.8.so.0[0x2b01d908864c]
[4] ?? in /lib/libpthread.so.0 [0x2b01d791c100]
[5] wxGIFDecoder::GetFrameSize(unsigned int) const in /usr/lib/libwx_gtk2u_core-2.8.so.0[0x2b01d89c6fba]
[6] wxGIFDecoder::ConvertToImage(unsigned int, wxImage*) const in /usr/lib/libwx_gtk2u_core-2.8.so.0[0x2b01d89c701c]
[7] wxTextCtrl::wxTextCtrl() in amule [0x5e4056]
[8] wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) in /usr/lib/libwx_baseu-2.8.so.0[0x2b01d908466f]
[9] wxEventHashTable::HandleEvent(wxEvent&, wxEvtHandler*) in /usr/lib/libwx_baseu-2.8.so.0[0x2b01d908480f]
[10] wxEvtHandler::ProcessEvent(wxEvent&) in /usr/lib/libwx_baseu-2.8.so.0[0x2b01d9084959]
[11] wxTimerBase::Notify() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0x2b01d8a0bd76]
[12] ?? in /usr/lib/libwx_gtk2u_core-2.8.so.0 [0x2b01d8902a14]
[13] ?? in /usr/lib/libglib-2.0.so.0 [0x2b01db32670b]
[14] g_main_context_dispatch in /usr/lib/libglib-2.0.so.0[0x2b01db325fd3]
[15] ?? in /usr/lib/libglib-2.0.so.0 [0x2b01db3292dd]
[16] g_main_loop_run in /usr/lib/libglib-2.0.so.0[0x2b01db3295ea]
[17] gtk_main in /usr/lib/libgtk-x11-2.0.so.0[0x2b01db925883]
[18] wxEventLoop::Run() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0x2b01d88fa50d]
[19] wxAppBase::MainLoop() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0x2b01d898bc8b]
[20] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.8.so.0[0x2b01d902380c]
[21] CryptoPP::IteratedHash<unsigned int, CryptoPP::EnumToType<CryptoPP::ByteOrder, 0>, 64u, CryptoPP::HashTransformation>::~IteratedHash() in amule [0x4e66a2]
[22] __libc_start_main in /lib/libc.so.6[0x2b01d9ab2b44]
[23] CryptoPP::BufferedTransformation::ChannelPut2(std::string const&, unsigned char const*, unsigned long, int, bool) in amule[0x441dc9]

--------------------------------------------------------------------------------[/I]

I put the same default address ([http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met](http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met)) in "Preferences button - Server - List" and "Auto-update server list at startup". But, when I restarted aMule:
*Failed to download the server list from*

I got a server.met from [web]("http://ed2k.2x4u.de/index.html") and replace my ~/.aMule/server.met. Now, 231 server were loaded, but *Servers - Trying to connect - Connection Lost*.

Does someone has the same problem?


Thanks a lot!

---

### Post by wavingpines on 2007-12-17
I downloaded aMule the other day and got the same thing.  I uninstalled it and gave up 'til tonight and thought I'd have another go.  I reinstalled using 'Applications-->Add/Remove' and it seems to work fine now!

May be worth de-/re-installing.  Synaptic shows I've got packages 'amule' and 'amule-common', both version 2.1.3-3-ubuntu1

---

### Post by Thiago Cesar Vieira on 2007-12-18
Ok wavingpines, thank you for your reply.
Hummm... I reinstalled but has the **same problem**.
Maybe package for **AMD64** has some bugs...

Thanks!

---

### Post by bengar on 2007-12-20
> **Thiago Cesar Vieira said:**
> Hi friends!

My aMule 2.13 is crashing after I click the button to update servers list. The link in Serverlist is default, I didn't changed:
[http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met](http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met)

When I run in console I can see bug messages:
[I]--------------------------------------------------------------------------------
A fatal error has occurred and aMule has crashed.
Please assist us in fixing this problem by posting the backtrace below in our
'aMule Crashes' forum and include as much information as possible regarding the
circumstances of this crash. The forum is located here:
    [http://forum.amule.org/board.php?boardid=67](http://forum.amule.org/board.php?boardid=67)
If possible, please try to generate a real backtrace of this crash:
    [http://www.amule.org/wiki/index.php/Backtraces](http://www.amule.org/wiki/index.php/Backtraces)

----------------------------=| BACKTRACE FOLLOWS: |=----------------------------
Current version is: aMule 2.1.3 using wxGTK2 v2.8.4 (Unicoded)
Running on: Linux 2.6.22-14-generic x86_64


** (amule:6869): CRITICAL **: clearlooks_style_draw_box_gap: assertion `height >= -1' failed
[2] wxThreadHelperThread::~wxThreadHelperThread() in amule [0x445575]
[3] wxFatalSignalHandler in /usr/lib/libwx_baseu-2.8.so.0[0x2b01d908864c]
[4] ?? in /lib/libpthread.so.0 [0x2b01d791c100]
[5] wxGIFDecoder::GetFrameSize(unsigned int) const in /usr/lib/libwx_gtk2u_core-2.8.so.0[0x2b01d89c6fba]
[6] wxGIFDecoder::ConvertToImage(unsigned int, wxImage*) const in /usr/lib/libwx_gtk2u_core-2.8.so.0[0x2b01d89c701c]
[7] wxTextCtrl::wxTextCtrl() in amule [0x5e4056]
[8] wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) in /usr/lib/libwx_baseu-2.8.so.0[0x2b01d908466f]
[9] wxEventHashTable::HandleEvent(wxEvent&, wxEvtHandler*) in /usr/lib/libwx_baseu-2.8.so.0[0x2b01d908480f]
[10] wxEvtHandler::ProcessEvent(wxEvent&) in /usr/lib/libwx_baseu-2.8.so.0[0x2b01d9084959]
[11] wxTimerBase::Notify() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0x2b01d8a0bd76]
[12] ?? in /usr/lib/libwx_gtk2u_core-2.8.so.0 [0x2b01d8902a14]
[13] ?? in /usr/lib/libglib-2.0.so.0 [0x2b01db32670b]
[14] g_main_context_dispatch in /usr/lib/libglib-2.0.so.0[0x2b01db325fd3]
[15] ?? in /usr/lib/libglib-2.0.so.0 [0x2b01db3292dd]
[16] g_main_loop_run in /usr/lib/libglib-2.0.so.0[0x2b01db3295ea]
[17] gtk_main in /usr/lib/libgtk-x11-2.0.so.0[0x2b01db925883]
[18] wxEventLoop::Run() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0x2b01d88fa50d]
[19] wxAppBase::MainLoop() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0x2b01d898bc8b]
[20] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.8.so.0[0x2b01d902380c]
[21] CryptoPP::IteratedHash<unsigned int, CryptoPP::EnumToType<CryptoPP::ByteOrder, 0>, 64u, CryptoPP::HashTransformation>::~IteratedHash() in amule [0x4e66a2]
[22] __libc_start_main in /lib/libc.so.6[0x2b01d9ab2b44]
[23] CryptoPP::BufferedTransformation::ChannelPut2(std::string const&, unsigned char const*, unsigned long, int, bool) in amule[0x441dc9]

--------------------------------------------------------------------------------[/I]

I put the same default address ([http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met](http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met)) in "Preferences button - Server - List" and "Auto-update server list at startup". But, when I restarted aMule:
*Failed to download the server list from*

I got a server.met from [web]("http://ed2k.2x4u.de/index.html") and replace my ~/.aMule/server.met. Now, 231 server were loaded, but *Servers - Trying to connect - Connection Lost*.

Does someone has the same problem?


Thanks a lot!

Hello Thiago
In those days I was searching why amule was not working. I had Gutsy before with  amule working fine, but now  I have a new PC, and amule was not working with the same problems like you. First you need to do is the configuration of  the settings like, auto connect on  startup, increase the bandwidth limits and make available both networks ED2K and Kademlia.
Then, is very important to remove the defaults links in the server to ED2K and the .dat in the Kad networks.

Remove this:
> [http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met](http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met)
For any of these:
 ```
[http://www.gruk.org/server.met.gz](http://www.gruk.org/server.met.gz)
[http://elboiler.p2pforum.it/server.met.gz](http://elboiler.p2pforum.it/server.met.gz)
```

Press the Server bottom for each new server link. Around 150 new server will be add. Also you can try adding new nodes in Kad removing the default server node.

Remove this:
> [http://download.overnet2000.de/nodes.dat](http://download.overnet2000.de/nodes.dat)

With any of these
 > [http://www.emule-inside.net/nodes.dat](http://www.emule-inside.net/nodes.dat)
[http://renololo1.free.fr/e/nodes.dat](http://renololo1.free.fr/e/nodes.dat)

I'll suggest you if still with connections problems use this link

> [http://www.amule.org/testport.php](http://www.amule.org/testport.php)

and test how it is working.

[IMG]http://i5.tinypic.com/8eghswo.png[/IMG]

[IMG]http://i13.tinypic.com/6teoent.png[/IMG]

Hope this help you or any one here.

---

### Post by Thiago Cesar Vieira on 2007-12-21
Hi bengar!

Thanks a lot for your reply.
Problem solved!! I followed your procedure (configuration) and aMule didn't crash and I could download some files.

Now, I'm trying to configure download rate. My link is download 1Mb/s and upload 500Kb/s. I put Download=200kB/s Upload=50kB/s and Slot Allocation=20kB/s.

Do you recommend a reference in Internet about "advanced" configuration?
I tried these ones:
[http://www.amule.org/wiki/index.php/FAQ_aMule#What_are_the_best_settings_I_can_set_to_have_a_nice_download_rate.3F](http://www.amule.org/wiki/index.php/FAQ_aMule#What_are_the_best_settings_I_can_set_to_have_a_nice_download_rate.3F)
[http://ubuntuforums.org/showthread.php?t=526975](http://ubuntuforums.org/showthread.php?t=526975)


Thanks again!!

---

### Post by bengar on 2007-12-23
> **Thiago Cesar Vieira said:**
> Hi bengar!

Thanks a lot for your reply.
Problem solved!! I followed your procedure (configuration) and aMule didn't crash and I could download some files.

Now, I'm trying to configure download rate. My link is download 1Mb/s and upload 500Kb/s. I put Download=200kB/s Upload=50kB/s and Slot Allocation=20kB/s.

Do you recommend a reference in Internet about "advanced" configuration?
I tried these ones:
[http://www.amule.org/wiki/index.php/FAQ_aMule#What_are_the_best_settings_I_can_set_to_have_a_nice_download_rate.3F](http://www.amule.org/wiki/index.php/FAQ_aMule#What_are_the_best_settings_I_can_set_to_have_a_nice_download_rate.3F)
[http://ubuntuforums.org/showthread.php?t=526975](http://ubuntuforums.org/showthread.php?t=526975)


Thanks again!!

Hi Cesar 
I am very happy because your amule is working.  I never had seen those references, the Hallvor's tutorials is sees excellent, but,  I use Synaptic is more ease to install all. The important thing here is remove those bad links and change it for a good one. About the download rate I just set it around  60 kb in download and 30kb in upload. Remember, if your connection status is in green colors in both networks, kad and Ed2k (see the picture) your amule is working and you don't need to do any more. Only share, share and share.
[IMG]http://i4.tinypic.com/7xsqk37.png[/IMG]

---

### Post by SpookyGhost on 2007-12-26
thank you to  bengar now my mule is working

---

### Post by bengar on 2007-12-28
> **SpookyGhost said:**
> thank you to  bengar now my mule is working
Ooh great this little tip is working for you Spooky. Also here is my complete working server list. copy and save it because was hard to collect it. Was test for me and work great, adding now around 300 servers.

**[COLOR="Red"]NEW SERVER LINK ALL WORKING[/COLOR]**
This is the same rule, when the amule was installed is necessary remove the default server link because it does not work.  > [http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met](http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met) For that reason will be replaced for one of  those links you see below. Remember one by one to increase your server list.

> [http://peerates.net/peerates/trueservers.met](http://peerates.net/peerates/trueservers.met)
[http://www.gruk.org/server.met.gz](http://www.gruk.org/server.met.gz) 
[http://users.servicios.retecal.es/ljpadillam/Baltab/server.met](http://users.servicios.retecal.es/ljpadillam/Baltab/server.met)
[http://usuarios.lycos.es/guillespi/server.met](http://usuarios.lycos.es/guillespi/server.met)
[http://elboiler.p2pforum.it/server.met.gz](http://elboiler.p2pforum.it/server.met.gz)



Also i find Ipfilter link. They are necessary to filter the fake servers. I test one and my amule does not work as before. In this case I change the port for 61000 for TCP and 61010 for UDP, next I see if it was making communication using the famous test link>  [http://www.amule.org/testport.php](http://www.amule.org/testport.php) and now is running again.

---

### Post by Thiago Cesar Vieira on 2008-01-06
Bengar, thank you again.

> Remember, if your connection status is in green colors in both networks, kad and Ed2k (see the picture) your amule is working and you don't need to do any more. Only share, share and share.

Ok. I saw the image that you send me. Sometimes mine has:
kad: firewalled (image yellow)
kad: off (image red)

When I start aMule, **Log** shows:
> 2008-01-06 11:08:18: Servers: Trying to connect
2008-01-06 11:08:18: Connecting to TVU DonkeyServer No1 (89.248.162.206 - 89.248.162.206:6543)
2008-01-06 11:08:18: Connected to Razorback 3.1 (193.138.205.25:5000)
2008-01-06 11:08:18: Connected to TVU DonkeyServer No1 (89.248.162.206:6543)
2008-01-06 11:08:26: **Warning: Razorback 3.1 (193.138.205.25:5000) - NG : You have a lowid. Please review your network config and/or your settings.**
2008-01-06 11:08:26: Servers: Connected
2008-01-06 11:08:26: Connection established with: Razorback 3.1
2008-01-06 11:08:28: **WARNING: You have recieved Low-ID!**
2008-01-06 11:08:28: 	Most likely this is because you're behind a firewall or router.
2008-01-06 11:08:28: 	For more information, please refer to [http://wiki.amule.org](http://wiki.amule.org)

Upload is ok because people can get my files, but my download is terrible.

I [tested]("http://www.amule.org/testport.php") my standard **port**, but I receved this error:
> Error: TCP port 61000 is unavailable. Make sure your firewall or router is allowing/forwarding this TCP service port and your ED2K client is running (i.e. aMule, eMule).
So, I changed TCP and UDP ports in aMule, like you said, and tried again. But I received the same error message.

My firewall is disabled, like we can see in result of command bellow
> $ sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

After that, I confirmed aMule **ports**
> $ netstat -lnptu | grep '/amule *$'
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:61000           0.0.0.0:*               LISTEN     7023/amule          
udp        0      0 0.0.0.0:61003           0.0.0.0:*                          7023/amule          
udp        0      0 0.0.0.0:61010           0.0.0.0:*                          7023/amule

Do you know why it occurs?


Thanks a lot!

---

### Post by bengar on 2008-01-13
> **Thiago Cesar Vieira said:**
> Bengar, thank you again.



Ok. I saw the image that you send me. Sometimes mine has:
kad: firewalled (image yellow)
kad: off (image red)

When I start aMule, **Log** shows:


Upload is ok because people can get my files, but my download is terrible.

I [tested]("http://www.amule.org/testport.php") my standard **port**, but I receved this error:

So, I changed TCP and UDP ports in aMule, like you said, and tried again. But I received the same error message.

My firewall is disabled, like we can see in result of command bellow


After that, I confirmed aMule **ports**


Do you know why it occurs?


Thanks a lot!

Hi Cesar 
Okay,  testing the Amule with the testport is the best way to know what is wrong. We need to discard the firewall, but,  Do you have a router connected in your system? that is another way to has a bad communications with the servers and many times is the reason to shown a low Id. Also you won't need to use the same port like me, Amule can run in any ports, but,  pay attention to the difference between the TCP and the UDP, I saw that UDP has a difference of 10 number more that the TCP, If you are using the port 10000 in TCP, the UDP most be 10010.

When I posted the last time I was playing with the IPfilter in the security section in the Amule. That produced a wrong configuration, after that, my Amule can not connected. I decided to uninstall the Amule but also I went to 
> places>home folder>view>Show Hide Files>
Amule folder will start with .Amule, I erased it and install again with synaptic.

Try to test in all the ports that you can, that was I done to finally, finding that the ports 61000 and 61010 are working for me now.



Then use again the testport tool. Cesar I will waiting for your results, waiting that this can help you.

---

### Post by eroeurbano on 2008-03-22
Hi, your advices were working
till I tried to share some directories,
after that, starting amule from terminal
i get errors like
Empty dir /home/luca/directory1 shared
Empty dir /home/luca/directory2 shared
Empty dir /home/luca/directory3 shared
for a big number of directories,
and it takes a lot lot of time to start, completely freezing
the whole system.
Of course the directories are not empty
and I can't figure out why I get those errors!

Can any of you guys help me?
Thanks a lot in advance and good easter ^_^
(if you celebrate it.. I don't :))

---

### Post by bengar on 2008-03-22
eroeurbano  
Hi tell me Why do you are using the terminal?

---

### Post by eroeurbano on 2008-03-23
I used terminal so that I could read warning and error messages...
the problems are the same if I don't use terminal...

---

