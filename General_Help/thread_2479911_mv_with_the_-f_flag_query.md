---
title: "mv with the -f flag query"
date: 2022-10-12
forum: General Help
---

### Post by Old Jimma on 2022-10-12
Hello Ubuntuers:



After a lifetime of coding, I have become aware of the importance of never removing anything. 

Better late than never, right?

I want to be certain about my interpretation of the **[COLOR="#FF0000"]-f[/COLOR]** flag used with the [COLOR="#FF0000"]**mv**[/COLOR] command. 

I think that when I use the -f flag, the mv command will REPLACE the old file with a new file, right??


Also, I"m a little slow to understand the zip utility. I want to use it NON-INTERACTIVELY with a password, encrypt, and back up all folders under the specified folder.

I use:

zip -P secretpassword -er directory.zip directory

I can't get this to work non-interactively. How do I fix this?

Thanks,
Very Old

---

### Post by #&amp;thj^% on 2022-10-12
> **Old Jimma said:**
> 

I want to be certain about my interpretation of the **[COLOR="#FF0000"]-f[/COLOR]** flag used with the [COLOR="#FF0000"]**mv**[/COLOR] command. 

I think that when I use the -f flag, the mv command will REPLACE the old file with a new file, right??



Yes it will overwrite the file
-f, --force
    do not prompt before overwriting

---

### Post by #&amp;thj^% on 2022-10-13
> **Old Jimma said:**
> Hello Ubuntuers:
Also, I"m a little slow to understand the zip utility. I want to use it NON-INTERACTIVELY with a password, encrypt, and back up all folders under the specified folder.

I use:

zip -P secretpassword -er directory.zip directory

I can't get this to work non-interactively. How do I fix this?

Thanks,
Very Old
You added more to your thread, I just noticed the above.
Kind of dirty work around, and I still use this method: [https://blog.gnu-designs.com/howto-quick-7-zip-trick-to-encrypt-your-files-with-non-interactive-mode/](https://blog.gnu-designs.com/howto-quick-7-zip-trick-to-encrypt-your-files-with-non-interactive-mode/)
At first after you have generated a strong password, use this "**example**"
```
cat your-pw-file | for i in *.xml; do 7z u -t7z -m0=lzma2 -mx=9 -mfb=64 -md=64m -ms=oi.7z $i -p --; done;

7-Zip [64] 17.04 : Copyright (c) 1999-2021 Igor Pavlov : 2017-08-28
p7zip Version 17.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,64 bits,16 CPUs x64)

Scanning the drive:
0 files, 0 bytes

Creating archive: *.xml.7z

Items to compress: 0


Enter password (will not be echoed):
Verify password (will not be echoed) :
    
Files read from disk: 0
Archive size: 32 bytes (1 KiB)
Everything is Ok

```
Change "your-pw-file" to your actual name used.
To verify that the files are properly encrypted and the right password works as expected, test as follows:

```

cat your-pw-file | for i in *.7z; do 7z t $i -p --; done;
```
Now I did not use any folder or file here, strictly for an example:
```
cat your-pw-file | for i in *.7z; do 7z t $i -p --; do

7-Zip [64] 17.04 : Copyright (c) 1999-2021 Igor Pavlov : 2017-08-28
p7zip Version 17.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,64 bits,16 CPUs x64)

Scanning the drive for archives:
1 file, 32 bytes (1 KiB)

Testing archive: *.xml.7z
--
Path = *.xml.7z
Type = 7z
Physical Size = 32
Headers Size = 0
Solid = -
Blocks = 0


No files to process
Everything is Ok

Files: 0
Size:       0
Compressed: 32


```
EDIT: I feel I need to add this statement:
WARNING: The encryption used by zip is not really a strong one. It can be cracked easily!
[list]

    [*]Now you can delete that password file from disk. I can&#8217;t stress this enough. Once you&#8217;ve used the password, and secured it in a managed password container, you&#8217;ll want to delete all traces of it that you do not need in plain sight on disk.

[*]That&#8217;s it. Now when you want to decompress those archives, you&#8217;ll need to supply the password you generated before. Make sure you keep this password secured in a managed location. A password is only as secure as your ability to manage it.[/list]

---

