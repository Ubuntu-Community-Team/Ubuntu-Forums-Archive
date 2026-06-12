---
title: "Autocomplete in browsers doesn't work on Linux"
date: 2016-02-08
forum: General Help
---

### Post by Lockheed on 2016-02-08
I have several websites which use autocomplete in their forms. For example, after logging in to an invoicing website I can type in the client field several letters (3-5) and then the box with list of client names will appear so that I can select one of them. There are many fields like that and all of them are supposed to work like this - I star typing and a list of matching positions appears so it can be selected

With my limited understanding of this autocomplete technology (mostly form googling for a solution) I suspect that it MIGHT be using javascript or jQuery, but I might be wrong.

There are three computers:
Computer A = Mac
Computer B = Ubuntu Linux
Computer C = Arch Linux (dualbooting with Windows 7)

Also, there are two networks:
Network Net1 = office network
Network Net2 = home network

Now, here is a very strange situation I am experiencing. 

On the Net1, those autocomplete forms work perfectly fine on A, and on C while on Windows. BUT they absolutely DO NOT work on B nor C while on linux - regardless the browser. When letters are typed in, on each website there is some animation that symbolises searching, but on Linux it runs infinitely, never getting any results, while on other systems it lasts less than a second before the list of proposed entries is displayed.

At the same time, autocomplete forms work just fine on B and C (Linux) while they are connected to ANY network OTHER than Net1 (that includes Net2, Net3, teetering from an android phones or GSM modem).

Net1 used to run on stock TP-Link router, but I flashed it with DD-WRT. No change whatsoever to autocomplete notworking on Linux. But then again - why should there be any change if all the time autocomplete worked fine on Mac and Windows...

So what could that be? Is it possible that for some arcane reason the ISP of Net1 blocks some packets responsible for autocomplete when it is for Linux clients? I really have not the faintest idea what could it be.

---

