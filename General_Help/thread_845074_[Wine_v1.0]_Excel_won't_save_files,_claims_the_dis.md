---
title: "[Wine v1.0] Excel won't save files, claims the disk is full"
date: 2008-06-30
forum: General Help
---

### Post by roccivic on 2008-06-30
I recently installed Excel 2003 in Wine 1.0, it works well, but I can't save anything as Excel claims the disk is full. I even tried to run it as root, but that didn't work out too well. The messages are "The disk is full" followed by "Document not saved"
I'm running Ubuntu 8.04 and I have the following DLL overrides installed in Wine:
```
riched20, native, windows
riched32, native, windows
msxml3, native, windows

```


This is the errors that are returned when Excel pops up the error messages (from the below error log):
```
fixme:storage:StgCreateStorageEx Stub: calling StgCreateDocfile, but ignoring pStgOptions and grfAttrs
fixme:storage:StorageImpl_CopyTo Exclude option not implemented
```


Here's the full error log:
```
user@user-pc:~$ env WINEPREFIX="/home/myusername/.wine" wine "C:\Program Files\Microsoft Office\OFFICE11\EXCEL.EXE" "Z:\mydatabase.xls"
fixme:powrprof:DllMain (0x7e350000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:win:EnumDisplayDevicesW ((null),0,0x32d710,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10042 0x00000000
fixme:storage:StorageImpl_Commit (0x14f7f0 5): stub
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000457,(nil),0x0001,0x00000000,0x7e5dc254,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime Optimization Service (clr_optimization_v2.0.50727_32) - Service reached limit of transient errors. Will shut down. Last error returned from Service Manager: 0x80070005.\n"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime Optimization Service"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000454,(nil),0x0001,0x00000000,0x7e5dc2c8,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:gdi:ExtCreatePen Hatches not implemented
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10026 0x00000000
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:reg:GetNativeSystemInfo (0x32fc00) using GetSystemInfo()
fixme:advapi:CheckTokenMembership ((nil) 0x1efa80 0x32fc08) stub!
fixme:advapi:CheckTokenMembership ((nil) 0x1efa80 0x32fc08) stub!
fixme:storage:StgCreateStorageEx Stub: calling StgCreateDocfile, but ignoring pStgOptions and grfAttrs
fixme:storage:StorageImpl_CopyTo Exclude option not implemented
fixme:imm:ImmReleaseContext (0x10026, 0x12cd98): stub
fixme:shell:IPersistFile_fnSaveCompleted (0x21fec8)->(L"C:\\windows\\profiles\\chc\\Recent\\Cork-06-07-wine.xls (6).lnk")
fixme:shell:DllCanUnloadNow stub
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x10042
```


Many thanks for your help, Rouslan

---

### Post by VMC on 2008-06-30
I don't have Excel installed. OpenOffice does just about everything and can save in Excel format.

I did have the disk is full on another Wine program. It ended up me changing to the d: directory somehow. Can you use the saveas function? Does the Configure Wine reveal any help?

Also did you check out our Wine sub-forum. Thre's many solutions found there.

---

### Post by LinuxRocks713 on 2008-08-18
Maybe your disk is actually full? Find out with:

```

sudo fdisk -l

```

and

```

df -h

```

---

### Post by BriLarks on 2008-11-29
I'm having the same problem. None of my disks are full.

---

### Post by gpsmikey on 2008-11-29
I may be wrong, but it seems to me that Excel will give that same error message if it can't write due to a permission problem.  Try saving the file to the /tmp directory which should allow you to do it.  If that works, it is a permission problem (assuming of course your disks are NOT full :)  )

mikey

---

### Post by fred! on 2009-01-03
I got the same problem (Disk full), but this only seems to occur when using a file that was created using OpenOffice. Native Excel files are saved correctly.

Fred

---

### Post by metapaso on 2009-02-10
I just encountered the same problem. Yes, I believe it is due to an openoffice.org created file.

As a workaround, I saved the document (in excel) as an "XML Spreadsheet format".  That allowed me to save it, then I saved again as a regular Excel Workbook (.xls) and everything appeared fine.

I don't know what the limits are of the xml spreadsheet format, but even my conditional formatting was preserved!  Yay.

As a note, I would prefer to be using openoffice.org, but I just filed a bug today because the COUNTIF function is broken in 3.0.1.

---

### Post by illlogic on 2009-02-13
I have a file that was saved by MS Works Spreadsheet, I believe version 8.5, that has the same problem as well. Other files save fine.

---

### Post by Mguel on 2009-08-08
> **metapaso said:**
>  As a workaround, I saved the document (in excel) as an "XML Spreadsheet format".  That allowed me to save it, then I saved again as a regular Excel Workbook (.xls) and everything appeared fine.

great! that made the trick for me, thanks!!!!

---

### Post by pietro2580 on 2009-10-07
I confirm that in my hands, it was also a OpenOffice file I tried to open in Excel.
Workaround by just copy past everything to a new excel file.
-- edit -- 
The xml workaround also works fine

---

### Post by dpatel on 2010-02-27
I know this is an old thread but in case anyone is still having the problem, I used winetricks to install dcom98 and vb6run and now I can open files created in OpenOffice using MS Excel 2003, modify it and save (no more disk full message).

I suspect it is the dcom98 that fixed the issue but since I also installed vb6run I can't be sure.

---

