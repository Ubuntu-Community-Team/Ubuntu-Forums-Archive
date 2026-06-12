---
title: "amule crashed after adding met file, feisty fawn"
date: 2007-04-23
forum: General Help
---

### Post by baosheng on 2007-04-23
Hi,

I have just deployed my Ubuntu 7.04 (Feisty Fawn) on my computer. I installed aMule as normal. But I found after I entered the URL containing an MET file and pressed ENTER key so that I can obtain ed2k server list, aMule crashed.

I followed this link

[http://www.amule.org/wiki/index.php/Getting_Started#Connecting_to_a_Server](http://www.amule.org/wiki/index.php/Getting_Started#Connecting_to_a_Server)

Following is my shell log:
forrest@medic:~$ amule
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
Loading temp files from /media/hda4/aMule/Temp.
Loading PartFile 1 of 1
All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672
Empty dir /media/hda4/aMule/Incoming/ shared
HTTP download thread started

--------------------------------------------------------------------------------
A fatal error has occurred and aMule has crashed.
Please assist us in fixing this problem by posting the backtrace below in our
'aMule Crashes' forum and include as much information as possible regarding the
circumstances of this crash. The forum is located here:
    [http://forum.amule.org/board.php?boardid=67](http://forum.amule.org/board.php?boardid=67)
If possible, please try to generate a real backtrace of this crash:
    [http://www.amule.org/wiki/index.php/Backtraces](http://www.amule.org/wiki/index.php/Backtraces)

----------------------------=| BACKTRACE FOLLOWS: |=----------------------------
Current version is: aMule 2.1.3 using wxGTK2 v2.8.1 (Unicoded)
Running on: Linux 2.6.20-15-generic i686

[2] wxThreadHelperThread::~wxThreadHelperThread() in amule [0x8084c8b]
[3] wxFatalSignalHandler in /usr/lib/libwx_baseu-2.8.so.0[0xb755b206]
[4] ?? in [0xffffe420]
[5] wxGIFDecoder::GetFrameSize(unsigned int) const in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb7812162]
[6] wxGIFDecoder::ConvertToImage(unsigned int, wxImage*) const in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb78121cc]
[7] wxTextCtrl::wxTextCtrl() in amule [0x823906d]
[8] wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const in /usr/lib/libwx_baseu-2.8.so.0[0xb74aed65]
[9] wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) in /usr/lib/libwx_baseu-2.8.so.0[0xb7556cbf]
[10] wxEventHashTable::HandleEvent(wxEvent&, wxEvtHandler*) in /usr/lib/libwx_baseu-2.8.so.0[0xb7556e0d]
[11] wxEvtHandler::ProcessEvent(wxEvent&) in /usr/lib/libwx_baseu-2.8.so.0[0xb7556f76]
[12] wxTimerBase::Notify() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb785dfe1]
[13] ?? in /usr/lib/libwx_gtk2u_core-2.8.so.0 [0xb7739555]
[14] ?? in /usr/lib/libglib-2.0.so.0 [0xb6f0d3c6]
[15] g_main_context_dispatch in /usr/lib/libglib-2.0.so.0[0xb6f0cdf2]
[16] ?? in /usr/lib/libglib-2.0.so.0 [0xb6f0fdcf]
[17] g_main_loop_run in /usr/lib/libglib-2.0.so.0[0xb6f10179]
[18] gtk_main in /usr/lib/libgtk-x11-2.0.so.0[0xb6cbd044]
[19] wxEventLoop::Run() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb772fd0c]
[20] wxAppBase::MainLoop() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb77d1cee]
[21] wxAppBase::OnRun() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb77d12e1]
[22] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.8.so.0[0xb74eb27a]
[23] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.8.so.0[0xb74eb327]
[24] CryptoPP::IteratedHash<unsigned int, CryptoPP::EnumToType<CryptoPP::ByteOrder, 0>, 64u, CryptoPP::HashTransformation>::~IteratedHash() in amule [0x812f490]
[25] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb721aebc]
[26] wxNotebook::SetPadding(wxSize const&) in amule[0x8080fd1]


--------------------------------------------------------------------------------
Aborted (core dumped)

---

### Post by kabuto_san on 2007-04-30
Hi all,
same problem for me....

Any idea?

---

### Post by kabuto_san on 2007-04-30
Ok,
I solved (4 me...)

1.) Open aMule -> Preference -> Server
2.) Select: "List" and copy this link: [http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met](http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met)
3.) Enable "Auto-Update serverlist at startup
4.) Close aMule and Open again

Now I can update my server list!!!

Kabu

---

### Post by benner on 2007-05-30
no server list.  then i click to update from

[http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met](http://ocbmaurice.dyns.net/pl/slist.pl?download/server-best.met)

and it crashes.

updating the KAD nodes crashes it too.

---

### Post by Hallvor on 2007-06-01
Just add the servers manually, then. Seriously, you only need a donkeyserver or two. You will still get results from clients connected to other servers.

EDIT: Be careful with adding serverlists you find online uncritically. They may contain fake servers controlled by RIAA/MPAA, and will not give any results when you search.

This list is safe: [http://www.gruk.org/list.php](http://www.gruk.org/list.php)

Add a couple of the largest servers.

---

