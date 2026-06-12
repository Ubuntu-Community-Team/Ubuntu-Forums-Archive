---
title: "Has java really installed in Wine?"
date: 2006-11-13
forum: General Help
---

### Post by Jongi on 2006-11-13
This is the console output when I install Sun Java in wine in Kubuntu Edgy

```

[jongi:~#] wine /mnt/Store/jre-1_5_0_09-windows-i586-p.exe
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
err:msi:msi_dialog_oncommand button click from nowhere 0x1ba880 67108864 0x10040
err:msi:msi_dialog_oncommand button click from nowhere 0x1ba880 67108864 0x10040
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"ValidateProductID"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveExistingProducts"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishComponents"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnpublishFeatures"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterTypeLibraries"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveODBC"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveRegistryValues"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterClassInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterExtensionInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterProgIdInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"UnregisterMIMEInfo"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveShortcuts"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveDuplicateFiles"
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"RemoveFolders"
err:msi:ITERATE_DuplicateFiles Failed to copy file L"c:\\Program Files\\Common Files\\Java\\Update\\Base Images\\jre1.5.0.b64\\patch-jre1.5.0_09.b03\\RegUtils.dll" -> L"c:\\Program Files\\Java\\jre1.5.0_09\\bin\\", last error 3
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"InstallODBC"
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:reg:GetNativeSystemInfo (0x7d201f40) using GetSystemInfo()

```

The program indicates it has installed successfully. Has it really?

---

### Post by aysiu on 2006-11-13
Why do you need Wine to install Java?

---

### Post by Jongi on 2006-11-13
Sorry, that's when I install java in wine

---

### Post by jordilin on 2006-11-13
you are trying to install the java windows version by means of wine. I would consider installing the java linux version which is found in java.sun.com and [follow these steps.]("http://jordilin.wordpress.com/2005/11/23/installing-java-in-ubuntu/")

---

### Post by mauserrifle on 2006-11-13
I think he's just wondering if java succesfully installed. Just to try on wine...

---

### Post by jordilin on 2006-11-13
> **mauserrifle said:**
> I think he's just wondering if java succesfully installed. Just to try on wine...

Yes it seems so, but it is not the right way of installing java in linux

---

### Post by mauserrifle on 2006-11-13
lol no. But some people find it funny to test these things.

---

### Post by Jongi on 2006-11-13
A program I am trying to install in wine requires java.

---

### Post by bucksgt on 2007-02-11
most of you seem to be missing the point here (and other threads regarding the same issue). of course you can run some jar natively in linux. i think the point is that there are some odd java/windows hybrid programs that need java inside wine.  the use jars and windows dlls executed out of an .exe.  the best way to do this is probably to configure the libraries using: winecfg

i haven't found any good specifics on how to do this for java. if anyone has any ideas, please share.

thanks,

-qk.

---

### Post by bucksgt on 2007-02-11
to install win32 jvm under wine:

  get a copy of advpack.dll (at the time of writing this, i went to: [http://www.dll-files.com/dllindex/dll-files.shtml?advpack](http://www.dll-files.com/dllindex/dll-files.shtml?advpack)  )

  unzip the file and copy the dll to ~/.winecfg/drive_c/Windows/system32/

  at the command prompt, type: winecfg
  
  click on the 'Libraries' tab

  under: New override for library:

  choose: advpack and click add

  i went to: [http://java.sun.com](http://java.sun.com) and downloaded 1.4.2 because that's what i needed for my app you should be able to use other versions.

  wine j2re-1_4_2_12-windows-i586-p.exe


-qk.

---

