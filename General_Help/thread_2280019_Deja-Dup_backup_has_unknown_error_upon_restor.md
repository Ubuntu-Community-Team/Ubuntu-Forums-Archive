---
title: "Deja-Dup backup has unknown error upon restor"
date: 2015-05-27
forum: General Help
---

### Post by matt174 on 2015-05-27
DISTRIB_DESCRIPTION="Ubuntu 14.04.2 LTS"

VERSION="14.04.2 LTS, Trusty Tahr"

After moving the backup from my external hard drive to a local folder on my new computer, I point Deja-Dup to the backup as follows:

```
sudo deja-dup --restore
```,

followed by the directory where I pasted the backup, and then choosing to restore to the original locations (the error I get happens with the choice to restore the backup into a specific folder as well).

This is the error:

```
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1494, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1488, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1337, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1422, in do_backup
    restore(col_stats)
  File "/usr/bin/duplicity", line 697, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 538, in Write_ROPaths
    ITR( ropath.index, ropath )
  File "/usr/lib/python2.7/dist-packages/duplicity/lazy.py", line 335, in __call__
    last_branch.fast_process, args)
  File "/usr/lib/python2.7/dist-packages/duplicity/robust.py", line 37, in check_common_error
    return function(*args)
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 591, in fast_process
    ropath.copy( self.base_path.new_index( index ) )
  File "/usr/lib/python2.7/dist-packages/duplicity/path.py", line 426, in copy
    other.writefileobj(self.open("rb"))
  File "/usr/lib/python2.7/dist-packages/duplicity/path.py", line 602, in writefileobj
    buf = fin.read(_copy_blocksize)
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 203, in read
    if not self.addtobuffer():
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 228, in addtobuffer
    self.tarinfo_list[0] = self.tar_iter.next()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 335, in next
    self.set_tarfile()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 324, in set_tarfile
    self.current_fp = self.fileobj_iter.next()
  File "/usr/bin/duplicity", line 733, in get_fileobj_iter
    backup_set.volume_name_dict[vol_num],
KeyError: 35
```

Really scared that an entire year's worth of work is down the drain now....

---

### Post by deadflowr on 2015-05-27
Deja Dup can fail, especially when running with sudo.
Perhaps try using duplicity, which is what deja dup is a frontend of.
Here's a good page on how you can use it:
[https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase](https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase)

See that method works.

---

### Post by RobGoss on 2015-05-27
I would recommend **Clonezilla** for creating ISO backups it works flawlessly.

---

### Post by matt174 on 2015-05-28
I am still getting some horrible errors. What else can I do?

```
TestDefaultLS.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/TestDefaultLSAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/TestDefaultParser.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/TestDefaultParserAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/TestGNUJAXP.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/TestGNUJAXPAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/TestJTidy.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/TestOracle.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/TestOracleAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/TestXerces.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/TestXercesAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/alltests.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/attrgetownerelement01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/attrgetownerelement02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/attrgetownerelement03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/attrgetownerelement04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/attrgetownerelement05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createAttributeNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createAttributeNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createAttributeNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createAttributeNS04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createAttributeNS05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createAttributeNS06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocument01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocument02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocument03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocument04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocument05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocument06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocument07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocument08.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocumentType01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocumentType02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocumentType03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createDocumentType04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createElementNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createElementNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createElementNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createElementNS04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createElementNS05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/createElementNS06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentcreateattributeNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentcreateattributeNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentcreateattributeNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentcreateattributeNS04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentcreateattributeNS05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentcreateattributeNS06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentcreateattributeNS07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentcreateelementNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentcreateelementNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentcreateelementNS05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentcreateelementNS06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentgetelementbyid01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentgetelementsbytagnameNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentgetelementsbytagnameNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentgetelementsbytagnameNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentgetelementsbytagnameNS04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentgetelementsbytagnameNS05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode08.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode09.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode10.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode11.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode12.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode13.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode14.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode15.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode17.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode18.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode19.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode20.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode21.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documentimportnode22.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documenttypeinternalSubset01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documenttypepublicid01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/documenttypesystemid01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/domimplementationcreatedocument03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/domimplementationcreatedocument04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/domimplementationcreatedocument05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/domimplementationcreatedocument07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/domimplementationcreatedocumenttype01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/domimplementationcreatedocumenttype02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/domimplementationcreatedocumenttype04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/domimplementationfeaturecore.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/domimplementationfeaturexmlversion2.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/domimplementationhasfeature01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/domimplementationhasfeature02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementgetattributenodens01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementgetattributenodens02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementgetattributenodens03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementgetattributens02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementgetelementsbytagnamens02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementgetelementsbytagnamens04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementgetelementsbytagnamens05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementhasattribute01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementhasattribute02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementhasattribute03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementhasattribute04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementhasattributens01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementhasattributens02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementhasattributens03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementremoveattributens01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributenodens01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributenodens02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributenodens03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributenodens04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributenodens05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributenodens06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributens01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributens02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributens03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributens04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributens05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributens08.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/elementsetattributensurinull.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getAttributeNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getAttributeNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getAttributeNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getAttributeNS04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getAttributeNS05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getAttributeNodeNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getAttributeNodeNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementById01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementById02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS08.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS09.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS10.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS11.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS12.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS13.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getElementsByTagNameNS14.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getNamedItemNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getNamedItemNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getNamedItemNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/getNamedItemNS04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hasAttribute01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hasAttribute02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hasAttribute03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hasAttribute04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hasAttributeNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hasAttributeNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hasAttributeNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hasAttributeNS04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hasAttributeNS05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hasAttributes01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hasAttributes02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hc_entitiesremovenameditemns1.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hc_entitiessetnameditemns1.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hc_namednodemapinvalidtype1.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hc_nodedocumentfragmentnormalize1.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hc_nodedocumentfragmentnormalize2.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hc_notationsremovenameditemns1.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/hc_notationssetnameditemns1.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode08.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode09.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode10.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode11.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode12.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode13.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode14.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode15.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode16.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/importNode17.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/internalSubset01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported09.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported10.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported11.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported12.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported13.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/isSupported14.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/localName01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/localName02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/localName03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/localName04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapgetnameditemns01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapgetnameditemns02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapgetnameditemns03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapgetnameditemns04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapgetnameditemns05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapgetnameditemns06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapremovenameditemns01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapremovenameditemns02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapremovenameditemns03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapremovenameditemns04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapremovenameditemns05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapremovenameditemns06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapremovenameditemns07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapremovenameditemns08.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapremovenameditemns09.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapsetnameditemns01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapsetnameditemns02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapsetnameditemns03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapsetnameditemns04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapsetnameditemns05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapsetnameditemns06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapsetnameditemns07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapsetnameditemns08.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapsetnameditemns09.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapsetnameditemns10.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namednodemapsetnameditemns11.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namespaceURI01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namespaceURI02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namespaceURI03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/namespaceURI04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodegetlocalname03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodegetnamespaceuri03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodegetownerdocument01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodegetownerdocument02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodegetprefix03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodehasattributes01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodehasattributes02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodehasattributes03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodehasattributes04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodeissupported01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodeissupported02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodeissupported03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodeissupported04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodeissupported05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodenormalize01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodesetprefix01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodesetprefix02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodesetprefix03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodesetprefix04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodesetprefix05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodesetprefix06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodesetprefix07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodesetprefix08.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/nodesetprefix09.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/normalize01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/ownerDocument01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/ownerElement01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/ownerElement02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/prefix01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/prefix02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/prefix03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/prefix04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/prefix05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/prefix06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/prefix07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/prefix08.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/prefix09.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/prefix10.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/prefix11.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/publicId01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/removeAttributeNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/removeAttributeNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/removeNamedItemNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/removeNamedItemNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/removeNamedItemNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNS04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNS05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNS06.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNS07.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNS09.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNS10.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNodeNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNodeNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNodeNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNodeNS04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setAttributeNodeNS05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setNamedItemNS01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setNamedItemNS02.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setNamedItemNS03.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setNamedItemNS04.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/setNamedItemNS05.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/core/systemId01.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/events because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/events/TestBatik.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/events/TestDefaultLS.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/events/TestDefaultLSAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/events/TestDefaultParser.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/events/TestDefaultParserAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/events/TestOracle.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/events/TestOracleAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/events/TestXerces.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/events/TestXercesAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/html because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/html/TestDefaultLS.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/html/TestDefaultLSAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level2/html/TestXercesHTML.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3 because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/core because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/core/TestBatik.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/core/TestDefaultLS.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/core/TestDefaultLSAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/core/TestDefaultParser.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/core/TestDefaultParserAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/core/TestOracle.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/core/TestOracleAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/core/TestXerces.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/core/TestXercesAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/ls because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/ls/TestBatik.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/ls/TestDefaultLS.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/ls/TestDefaultParser.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/ls/TestOracle.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/ls/TestXerces.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/validation because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/validation/TestBatik.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/validation/TestDefaultLS.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/validation/TestDefaultLSAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/validation/TestDefaultParser.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/validation/TestDefaultParserAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/validation/TestOracle.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/validation/TestOracleAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/xpath because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/xpath/TestBatik.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/xpath/TestDefaultLS.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/xpath/TestDefaultLSAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/xpath/TestDefaultParser.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/xpath/TestDefaultParserAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/xpath/TestXalan.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/w3c/domts/level3/xpath/TestXalanAltConfig.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/AttributeList.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/Attributes.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/ContentHandler.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/DTDHandler.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/DocumentHandler.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/EntityResolver.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/ErrorHandler.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/HandlerBase.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/InputSource.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/Locator.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/Parser.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/SAXException.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/SAXNotRecognizedException.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/SAXNotSupportedException.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/SAXParseException.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/XMLFilter.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/XMLReader.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/ext because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/ext/Attributes2.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/ext/Attributes2Impl.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/ext/DeclHandler.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/ext/DefaultHandler2.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/ext/EntityResolver2.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/ext/LexicalHandler.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/ext/Locator2.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/ext/Locator2Impl.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers/AttributeListImpl.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers/AttributesImpl.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers/DefaultHandler.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers/LocatorImpl.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers/NamespaceSupport.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers/NewInstance.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers/ParserAdapter.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers/ParserFactory.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers/XMLFilterImpl.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers/XMLReaderAdapter.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xml/sax/helpers/XMLReaderFactory.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xmlpull because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xmlpull/v1 because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xmlpull/v1/XmlPullParser.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xmlpull/v1/XmlPullParserException.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xmlpull/v1/XmlPullParserFactory.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xmlpull/v1/XmlSerializer.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xmlpull/v1/sax2 because of previous error
Skipping home/matias/.android-sdks/sources/android-21/org/xmlpull/v1/sax2/Driver.java because of previous error
Skipping home/matias/.android-sdks/sources/android-21/source.properties because of previous error
Skipping home/matias/.android-sdks/system-images because of previous error
Skipping home/matias/.android-sdks/system-images/android-21 because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/armeabi-v7a because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/armeabi-v7a/NOTICE.txt because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/armeabi-v7a/build.prop because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/armeabi-v7a/devices.xml because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/armeabi-v7a/hardware.ini because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/armeabi-v7a/kernel-qemu because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/armeabi-v7a/ramdisk.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/armeabi-v7a/source.properties because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/armeabi-v7a/system.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/armeabi-v7a/userdata.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/x86 because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/x86/NOTICE.txt because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/x86/build.prop because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/x86/devices.xml because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/x86/hardware.ini because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/x86/kernel-qemu because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/x86/ramdisk.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/x86/source.properties because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/x86/system.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-tv/x86/userdata.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/NOTICE.txt because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/build.prop because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/devices.xml because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/hardware.ini because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/kernel-qemu because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/ramdisk.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearRound because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearRound/button.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearRound/circle_mask_320px.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearRound/circle_mask_380px.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearRound/circle_mask_380px_onion.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearRound/controls.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearRound/hardware.ini because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearRound/layout because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearRound/palm_button.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearRound/palm_controls.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearSquare because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearSquare/button.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearSquare/controls.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearSquare/hardware.ini because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearSquare/layout because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearSquare/palm_button.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/skins/AndroidWearSquare/palm_controls.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/source.properties because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/system.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/armeabi-v7a/userdata.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86 because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/NOTICE.txt because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/build.prop because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/devices.xml because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/kernel-qemu because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/ramdisk.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearRound because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearRound/button.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearRound/circle_mask_320px.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearRound/circle_mask_380px.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearRound/circle_mask_380px_onion.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearRound/controls.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearRound/hardware.ini because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearRound/layout because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearRound/palm_button.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearRound/palm_controls.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearSquare because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearSquare/button.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearSquare/controls.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearSquare/hardware.ini because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearSquare/layout because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearSquare/palm_button.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/skins/AndroidWearSquare/palm_controls.png because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/source.properties because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/system.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/android-wear/x86/userdata.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/default because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/default/armeabi-v7a because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/default/armeabi-v7a/NOTICE.txt because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/default/armeabi-v7a/build.prop because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/default/armeabi-v7a/hardware.ini because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/default/armeabi-v7a/kernel-qemu because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/default/armeabi-v7a/ramdisk.img because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/default/armeabi-v7a/source.properties because of previous error
Skipping home/matias/.android-sdks/system-images/android-21/default/armeabi-v7a/system.img because of previous error
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1494, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1488, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1337, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1422, in do_backup
    restore(col_stats)
  File "/usr/bin/duplicity", line 697, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 536, in Write_ROPaths
    for ropath in rop_iter:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 500, in integrate_patch_iters
    for patch_seq in collated:
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 380, in yield_tuples
    setrorps( overflow, elems )
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 369, in setrorps
    elems[i] = iter_list[i].next()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 120, in difftar2path_iter
    multivol_fileobj.close() # aborting in middle of multivol
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 240, in close
    if not self.addtobuffer():
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 228, in addtobuffer
    self.tarinfo_list[0] = self.tar_iter.next()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 335, in next
    self.set_tarfile()
  File "/usr/lib/python2.7/dist-packages/duplicity/patchdir.py", line 324, in set_tarfile
    self.current_fp = self.fileobj_iter.next()
  File "/usr/bin/duplicity", line 733, in get_fileobj_iter
    backup_set.volume_name_dict[vol_num],
KeyError: 35

matt@matt-Aspire-E3-111:~/Documents/acer-full-restore/another-try$ 
 
```

---

