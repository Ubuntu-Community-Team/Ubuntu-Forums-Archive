---
title: "Script to decode FileZilla Base 64 passwords on ubuntu?"
date: 2021-05-24
forum: General Help
---

### Post by dbee on 2021-05-24
So I've been messing around with a script to read the FileZilla.xml settings file and automatically parse the file for passwords. 

Then decode those passwords and output them, labelled, on a newline...

This is what I've gotten so far..
```

# Parse Filezilla passwords and decode from base64                                                                                                                                                                                                                                            
ftp_decode() {
    sed -n 's/^.*base64">\(.*\)<\/Pass>$/\1/mp' /home/dara/.config/filezilla/sitemanager.xml | base64 --decode
}

```
Now what i want to do is to output them all on a newline and label them ie.
```

MySite1: mypass
MySite2: mypass1
MySIte3: mypass2

```
This is an example of a FileZilla.xml file...
```

<FileZilla3 version="3.46.3" platform="*nix">
<Servers>
<Server>
<Host>*******</Host>
<Port>21</Port>
<Protocol>0</Protocol>
<Type>0</Type>
<User>******</User>
<Pass encoding="base64">Mypass</Pass>
<Logontype>1</Logontype>
<TimezoneOffset>0</TimezoneOffset>
<PasvMode>MODE_DEFAULT</PasvMode>
<MaximumMultipleConnections>0</MaximumMultipleConnections>
<EncodingType>Auto</EncodingType>
<BypassProxy>0</BypassProxy>
<Name>MySite</Name>
<Comments></Comments>
<Colour>0</Colour>
<LocalDir/>
<RemoteDir/>
<SyncBrowsing>0</SyncBrowsing>
<DirectoryComparison>0</DirectoryComparison>
</Server>

```
Can anyone help? I'd prefer to use native bash rather than perl.

---

### Post by dragonfly41 on 2021-05-24
I find ripgrep to be useful ..

for your scenario ...

[FONT=monospace][COLOR=#5454FF]**~/.config/filezilla**[/COLOR][COLOR=#000000]$ rg -i encoding="base64"

might be one search pattern to start with.
But you will need to format your output.
[/COLOR]
[/FONT]

---

### Post by dbee on 2021-05-31
> **dragonfly41 said:**
> I find ripgrep to be useful ..

for your scenario ...

[FONT=monospace][COLOR=#5454FF]**~/.config/filezilla**[/COLOR][COLOR=#000000]$ rg -i encoding="base64"

might be one search pattern to start with.
But you will need to format your output.
[/COLOR]
[/FONT]

Thanks dragonfly,

Not sure that ripgrep is what I'm looking for to be honest.

At the moment, I'm getting the decoded passwords for all my sites...

> 
mypass1mypass2mypass3mypass4


what I want is something like this...

> 
MYSITE1: mypass1
MYSITE2: mypass2
MYSITE3: mypass3
MYSITE4: mypass4


Any bash/sed experts out there that can help?

---

