---
title: "Amule starts and immediately closes"
date: 2006-07-04
forum: General Help
---

### Post by isenalim on 2006-07-04
Hi,
I am in trouble with amule. I installed it via synaptic with the standard repositories and all universe and multiverse and so on activated.
I click on the icon and amule starts but after 2 seconds showing me the server list it closes.

This is the output I get when launching from the terminal,
thank you everybody!

```
(process:23177): Gdk-WARNING **: locale not supported by Xlib

(process:23177): Gdk-WARNING **: cannot set locale modifiers
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
Loading temp files from /home/beppe/.aMule/Temp.

All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672
Empty dir /home/beppe/.aMule/Incoming shared

--------------------------------------------------------------------------------A fatal error has occurred and aMule has crashed.
Please assist us in fixing this problem by posting the backtrace below in our
'aMule Crashes' forum and include as much information as possible regarding the
circumstances of this crash. The forum is located here:
    http://forum.amule.org/board.php?boardid=67
If possible, please try to generate a real backtrace of this crash:
    http://www.amule.org/wiki/index.php/Backtraces

----------------------------=| BACKTRACE FOLLOWS: |=----------------------------Current version is: aMule 2.1.0 using wxGTK2 v2.6.1 (Unicoded)
Running on: Linux 2.6.15-25-686 i686

[2] wxThreadHelperThread::~wxThreadHelperThread() in amule [0x80811e3]
[3] wxFatalSignalHandler in /usr/lib/libwx_baseu-2.6.so.0[0xb76326ea]
[4] ?? in [0xffffe420]
[5] wxString::CmpNoCase(wxString const&) const in /usr/lib/libwx_baseu-2.6.so.0[0xb75f8c55]
[6] wxMenuItemList::~wxMenuItemList() in amule [0x81740b4]
[7] wxWindowDC::CanGetTextExtent() const in amule [0x8227f44]
[8] wxMenuItemList::~wxMenuItemList() in amule [0x8177752]
[9] wxMenuItemList::~wxMenuItemList() in amule [0x8178d3b]
[10] CryptoPP::IteratedHashBase2<unsigned int, CryptoPP::EnumToType<CryptoPP::ByteOrder, 0>, CryptoPP::HashTransformation>::~IteratedHashBase2() in amule [0x8128bb0]
[11] wxThreadHelperThread::~wxThreadHelperThread() in amule [0x80829d2]
[12] wxTopLevelWindowGTK::GetTitle() const in amule [0x80fba1a]
[13] wxTopLevelWindowGTK::GetTitle() const in amule [0x80fd6c3]
[14] std::vector<bool, std::allocator<bool> >::_M_fill_insert(std::_Bit_iterator, unsigned int, bool) in amule [0x80c515b]
[15] wxTopLevelWindowGTK::GetTitle() const in amule [0x80f99ec]
[16] wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const in /usr/lib/libwx_baseu-2.6.so.0[0xb75a62a1]
[17] wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) in /usr/lib/libwx_baseu-2.6.so.0[0xb762e97f]
[18] wxEventHashTable::HandleEvent(wxEvent&, wxEvtHandler*) in /usr/lib/libwx_baseu-2.6.so.0[0xb762eb50]
[19] wxEvtHandler::ProcessEvent(wxEvent&) in /usr/lib/libwx_baseu-2.6.so.0[0xb762ed01]
[20] wxEvtHandler::ProcessPendingEvents() in /usr/lib/libwx_baseu-2.6.so.0[0xb762f2d1]
[21] wxAppConsole::ProcessPendingEvents() in /usr/lib/libwx_baseu-2.6.so.0[0xb75a656a]
[22] ?? in /usr/lib/libwx_gtk2u_core-2.6.so.0 [0xb77923a2]
[23] ?? in /usr/lib/libglib-2.0.so.0 [0xb6d46bf2]
[24] g_main_context_dispatch in /usr/lib/libglib-2.0.so.0[0xb6d448d6]
[25] ?? in /usr/lib/libglib-2.0.so.0 [0xb6d47996]
[26] g_main_loop_run in /usr/lib/libglib-2.0.so.0[0xb6d47cb8]
[27] gtk_main in /usr/lib/libgtk-x11-2.0.so.0[0xb717f775]
[28] wxEventLoop::Run() in /usr/lib/libwx_gtk2u_core-2.6.so.0[0xb77ab324]
[29] wxAppBase::MainLoop() in /usr/lib/libwx_gtk2u_core-2.6.so.0[0xb783ab2a]
[30] wxAppBase::OnRun() in /usr/lib/libwx_gtk2u_core-2.6.so.0[0xb783ac0f]
[31] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.6.so.0[0xb75d9a44]
[32] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.6.so.0[0xb75d9af8]
[33] CryptoPP::IteratedHashBase2<unsigned int, CryptoPP::EnumToType<CryptoPP::ByteOrder, 0>, CryptoPP::HashTransformation>::~IteratedHashBase2() in amule [0x81276cc]
[34] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb734dea2]
[35] __gxx_personality_v0 in amule[0x807dad1]


--------------------------------------------------------------------------------Aborted

```

---

