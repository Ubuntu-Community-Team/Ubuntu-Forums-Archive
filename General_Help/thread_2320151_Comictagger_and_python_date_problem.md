---
title: "Comictagger and python date problem"
date: 2016-04-11
forum: General Help
---

### Post by Bo Rosén on 2016-04-11
Hi all!

I'm having a problem with comictagger not being able to open files due to some sort of problem with how python handles dates. My locale is set to Sweden and I'm running Ubuntu 15.10.
I've had this problem earlier, but can't remember how to fix it, or find the solution again.

Any ideas?
Thanks

```
Traceback (most recent call last):  File "/usr/local/lib/python2.7/dist-packages/comictaggerlib/taggerwindow.py", line 917, in selectFolder
    self.selectFile( folder_mode=True )
  File "/usr/local/lib/python2.7/dist-packages/comictaggerlib/taggerwindow.py", line 946, in selectFile
    self.fileSelectionList.addPathList( fileList )
  File "/usr/local/lib/python2.7/dist-packages/comictaggerlib/fileselectionlist.py", line 196, in addPathList
    row = self.addPathItem( f )
  File "/usr/local/lib/python2.7/dist-packages/comictaggerlib/fileselectionlist.py", line 271, in addPathItem
    if ca.seemsToBeAComicArchive() :
  File "/usr/local/lib/python2.7/dist-packages/comictaggerlib/comicarchive.py", line 618, in seemsToBeAComicArchive
    ( self.getNumberOfPages() > 0)
  File "/usr/local/lib/python2.7/dist-packages/comictaggerlib/comicarchive.py", line 775, in getNumberOfPages
    self.page_count = len( self.getPageNameList( ) )
  File "/usr/local/lib/python2.7/dist-packages/comictaggerlib/comicarchive.py", line 751, in getPageNameList
    files = self.archiver.getArchiveFilenameList()
  File "/usr/local/lib/python2.7/dist-packages/comictaggerlib/comicarchive.py", line 395, in getArchiveFilenameList
    for item in rarc.infolist():
  File "/usr/local/lib/python2.7/dist-packages/comictaggerlib/UnRAR2/__init__.py", line 127, in infolist
    return list(self.infoiter())
  File "/usr/local/lib/python2.7/dist-packages/comictaggerlib/UnRAR2/__init__.py", line 122, in infoiter
    for params in RarFileImplementation.infoiter(self):
  File "/usr/local/lib/python2.7/dist-packages/comictaggerlib/UnRAR2/unix.py", line 171, in infoiter
    data['datetime'] = time.strptime(fields[2]+" "+fields[3], '%d-%m-%y %H:%M')
  File "/usr/lib/python2.7/_strptime.py", line 467, in _strptime_time
    return _strptime(data_string, format)[0]
  File "/usr/lib/python2.7/_strptime.py", line 325, in _strptime
    (data_string, format))
ValueError: time data '2010-08-11 12:59' does not match format '%d-%m-%y %H:%M'



```

---

