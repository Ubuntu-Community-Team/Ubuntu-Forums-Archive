---
title: "How to use MlDonkey in Gutsy"
date: 2007-11-13
forum: General Help
---

### Post by mlinchits on 2007-11-13
I am using an updated version of Kubuntu Gutsy Gibbon. For some reason no servers show up when I open Kmldonkey and the search option produces no results. Status bar says "connected admin@localhost". MlDonkey has been installed and "mlnet" identified.

The program used to work automatically in Feisty.

Any suggestioons?

Thanks

---

### Post by mlinchits on 2007-11-13
Also Ktorrents has ceased to work: downloads become stalled. Maybe its related to the problem with Kmldonkey.

I think the problem is with Kubuntu Gutsy in general.

---

### Post by taj on 2007-12-01
The problem may be in a bug in gutsy.

In feisty and earlier I used to be able to run the mlnet executable from sourceforge without a problem. After my upgrade I get this output:
:~$ ~/mldonkey-distrib-2.9.2/mlnet
2007/12/01 13:03:38 [cO] Starting MLDonkey 2.9.2 ...
2007/12/01 13:03:38 [cO] Language EN, locale ANSI_X3.4-1968, ulimit for open files 1024
2007/12/01 13:03:38 [cO] MLDonkey is working in .
2007/12/01 13:03:38 [Gettext] Loading language resource mlnet_strings.en_US.UTF-8
2007/12/01 13:03:38 [cO] loaded language resource file
2007/12/01 13:03:38 [DNS] Resolving [host] ...
2007/12/01 13:03:39 [DNS] Resolving [[www.mldonkey.org]](www.mldonkey.org]) ...
Floating point exception (core dumped)

This also happens when I try to run mlnet version 2.8.1
Again, both executables ran without a problem in feisty

I googled some posts on this issue, but unfortunately they are all asian websites (that I cannot read) :(

---

### Post by kochakaden on 2008-01-10
The links from Google are mostly Chinese, but basically they're saying that the binaries from the mldonkey site are broken, and you have to download the sources and compile yourself.  Pretty straightforward:  extract the tarball, run ./configure, run make, copy the resulting mlnet somewhere on your path.

I just did that and it works fine now (though I have to load it manually - the initd script still doesn't work).  Say "yes" when it asks if it should compile a local copy of ocaml.

---

