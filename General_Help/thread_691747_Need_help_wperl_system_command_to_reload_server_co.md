---
title: "Need help w/perl system command to reload server conf"
date: 2008-02-08
forum: General Help
---

### Post by einstein on 2008-02-08
Greetings;

I have written a perl script to monitor my router's gateway address, compare it with pasv_address in vsftpd.conf and, if different, modify the conf and reload the conf file.  I am using something like:
```

@sysargs=('/etc/init.d/vsftpd','force-reload');

if(system(@sysargs)==0){
	$ret = 1;
}
else{
	print "Error: $?\n";
	$ret = 0;
}
...

```
A little bit strangely it worked for a while but then stopped - returning error 256.

Can anyone tell me:
[LIST=1]
[*]Is my code correct?  I know it is a little ugly but I need to do some other stuff in the if or else so do or die doesn't work very well.
[*]Am I even using the correct perl command (I have to get a return value indicating success or failure)
[*]What the error code 256 means?
[/LIST]
I have spent a lot of hours (days?) trying to make my ftp server accessible from the Internet.  Reloading the ftp server configuration is the last hiccup.  Unfortunately, I do not know anything about shell scripts.

Any insights offered would be much appreciated.

Best regards,
              Dennis

---

### Post by einstein on 2008-02-09
Never mind.  I found a better way.  See [http://ubuntuforums.org/showthread.php?t=692355](http://ubuntuforums.org/showthread.php?t=692355)

Dennis

---

