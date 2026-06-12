---
title: "Using Command Line Avast Virus Scanner"
date: 2007-05-20
forum: General Help
---

### Post by Craftycorner on 2007-05-20
> # man avast

This will give you the command and options.

Open a Konsole and type "man avast"


virgule@monpc:~$ avast --help
Usage: avast [OPTION...] <areaname...>
avast v1.0.6 -- command-line virus scanner

Options:
  -_, --console              Application will be working in STDIN/STDOUT mode
  -a, --testall              Test all of the files (default)
  -b, --blockdevices         Scan block devices
  -c, --testfull             Scan entire files
  -d, --directory            Scan only directory content
  -i, --ignoretype           Ignore virus sets
  -n, --nostats              No virus check statistics
  -p, --continue=1234        Automatic action with infected file:
                             1:delete, 2:(not supported), 3:repair, 4:stop
  -r, --report=

    * file       Create report file, '*' for OK results

  -t, --archivetype[=ZGBTIJRXOQHFVPYD6UWAN]   Scan archives: Z:ZIP(default),
                             G:GZ(default), B:BZIP2(default), T:TAR(default),
                             I:MIME, J:ARJ, R:RAR, X:Exec(default), O:ZOO,
                             Q:ARC, H:LHA, F:TNEF, V:CPIO, P:RPM, Y:ISO,
                             D:DBX, 6:SIS, U:OLE, W:WINEXEC(default), A:All,
                             N:None
  -v, --viruslist=mask       Show list of all specific viruses
  -h, --help                 Give this help list
      --usage                Give a short usage message
  -V, --version              Print program version

Mandatory or optional arguments to long options are also mandatory or optional
for any corresponding short options.

Report bugs to <support@avast.com>.

What I need to know is how to UPDATE the antivirus via the command line.

Thanks.:D

---

### Post by zvacet on 2007-05-20
You can try** --usage** command and see what will it tell you.I don´t think you realy need this,because Avast comes with GUI and there you can select automatic option for update.

---

### Post by rakku-toki telkio-kuuni on 2007-05-21
"avast-update" in terminal

---

