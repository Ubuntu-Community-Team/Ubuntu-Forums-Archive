---
title: "Write permission problem on Windows with Linux Samba share"
date: 2014-02-06
forum: General Help
---

### Post by roooii on 2014-02-06
Hello everyone,

I'm playing around with this odd problem for quite a while now and haven't been able to find any solution. There's no information on the internet. So I hope someone can finally help me out.

I got Samba configured on my Linux server. I'm using a Samba share on a Windows client (on my Windows machine I added it as network-drive "Y:" ). So far everything is working perfectly. I can create files and directories and the permissions specified in smb.conf are applying correctly. Until this point manually adding files on my Y: drive works without a doubt.

But I got this pear-module called PhpDocumentor. I believe it uses php.exe on my Windows machine to create documentation for Php projects. First it starts creating a few folders and copying a few files to the desired folder on the Y: drive. This is working fine and the permissions for those folders and files are also correct.

But the next step I get this permissions error. And from what I believe it is trying to run php.exe or pear. 

```
unable to write to $compile_dir 'Y:\projects\classes\database\documentation\phpdoc\media\26d3399f63abd43a7d72f8c21440dcb0'. Be sure $compile_dir is writable by the web server user.
```

Is it possible that php.exe is running as the SYSTEM user (and not as the user logged in on the Samba share) on my Windows machine and could that be causing the write permission errors on my Linux samba share?

Could anyone explain to me what is happening here? I would be very greatful.

It's kinda hard to explain what the problem is, so if there's any missing information I'd be happy to give more information.

Best regards.

---

### Post by roooii on 2014-02-07
No one who could help me out? :(

---

