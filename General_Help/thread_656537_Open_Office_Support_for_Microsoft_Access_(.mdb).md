---
title: "Open Office Support for Microsoft Access (.mdb)"
date: 2008-01-02
forum: General Help
---

### Post by Mark Erbaugh on 2008-01-02
In Open Office 2.0 Base that comes with Dapper (6.06), under "Connect to an existing database" has an option "Microsoft Access" that can open Microsoft Access Database (.mdb) files.

In Open Office Office 2.3 base that comes with Gutsy (7.10), this option is not there.  Poking around in OO, it looks like the driver:

org.openoffice.comp.connectivity.mdb.Driver

is not there. 

I don't remember installing a specific package to add this driver to 2.0.

---

### Post by jeffus_il on 2008-01-02
Install mdbtools, should do the trick for you.
and mdbtools-gmdb looks like a neat tool for gnome users.

---

### Post by Mark Erbaugh on 2008-01-03
According to the package manager mdbtools is installed and still no support for mdb files in Open Office

---

### Post by jeffus_il on 2008-01-03
Sorry it seems that OO is still planning the driver, want to write it?

**Native, cross-platform access to MS Access         databases**

       **description**

       *preliminary note*: In the meantime, there is an alpha version of a driver for this.       It's an OOo database driver which uses [MDB Tools]("http://mdbtools.sourceforge.net/") to       read MS Access databases. See [it's home page]("http://dba.openoffice.org/drivers/mdb/index.html") for more info.
        A major goal of OpenOffice.org is interoperability with other office       applications, especially with a certain office suite which currently has some greater market share than       OpenOffice.org has :).
        Unfortunately, currently OOo users, as long as they don't work on Windows, are not able *at all*       to access the databases of this office suite - we cannot read MDB files on platforms other than Windows       (where we can use Microsofts own API).
        So the goal here is to allow Linux users to at least read the data from MDB files, using OOo.
        There are several ways how this could be done.
      One is to use MDB Tools, and wrap them in OOo. Since the SQL capabilities of the MDB Tools parser are       limited (e.g., no OR conditions in WHERE clauses are allowed), this requires work in either MDB Tools       itself (by improving their parser), or it would be used as provider for raw data, and OOo would faciliate       it's own parser/query engine (which unfortunately is also limited) to process this data.
      Another current disadvantage of MDB Tools is that it doesn't handle UTF8, and since jet4 databases       stored their data in UTF8, this implies that it cannot be used for jet4 databases containing non-ASCII       characters (well, probably a little bit more that ASCII, but it's a serious limitation for an product as       international as OpenOffice.org).
        Another way would be to re-engineer the MDB format ourself, and write a native SDBC driver (which could       be in C++ or probably even in Java) which provides the data. This is similar to the first approach, where       MDB Tools would have been used as the provider of raw data.
                                         required skills                            [LIST]
[*]C++[/LIST]                                                useful skills                            [LIST]
[*]familarity with OOo's database access API[/LIST]                                                estimated effort             2 months                                   difficulty             medium

---

### Post by Mark Erbaugh on 2008-01-04
I wonder why/how MDB support worked in OO 2.0?

---

### Post by fr4gm0nk3y on 2008-01-11
Is there any update on this? I need .mdb access on my ubuntu system =(

---

### Post by the_darkside_986 on 2008-01-25
Yeah really... Microsh*t really needs to be sued more for pulling this kind of crap. I mean, the mdb I'm trying to open is simply a couple of tables for an assignment. It contains no information about the Windows operating system, so there is not a single damned reason why it should require OS-specific junk. 

I'm actually on openSUSE, a distro known for its specialized OO version that handles Office 2007 files, but I still can't get this to work. I tried booting into Windows and exporting it to *.odb via the Windows version of OO but when I copy the resulting file to my Linux partition, I still can't access the tables without some error message. I don't see why it can't just export all the tables and data into a fresh file without trying to worry about some "data provider" bulls***. 

This is the reason why I export all my mp3's to vorbis, all my doc's to *.odf, etc. (I even run a homebrew application for playing oggs on my PSP since mp3s waste all my limited disk space.) One time, I made my friend download OpenOffice for Windows in order to view some files I had converted. And he did. But he is on Ubuntu now so that's not a problem.

---

### Post by vd2144 on 2008-01-30
Hi,

Do you know if open office has the same 255 col limit that MS access has?
Also, when I open a MS access database with open office, it only reads the tables and not queries.
Do I have to recode everything or is there a way to fix that?

Thx!!!!

Vincent.

---

### Post by amlucent23 on 2008-07-13
I dont understand. [This functionality was available]("http://salahuddin66.blogspot.com/2007/09/mdb-file-in-openofficeorg.html") in oo-base and now I cant find any way to add this to Hardy.

---

