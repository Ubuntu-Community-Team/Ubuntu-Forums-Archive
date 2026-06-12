---
title: "$HOME/.dmrc file is being ignored when logging in"
date: 2007-05-06
forum: General Help
---

### Post by cbrad on 2007-05-06
I have tried all the chown and chmod ways and still am unable to log into ubuntu 7.04

one of the lines I have tried is 

chown -R username $HOME/.dmrc
chmod 644 $HOME/.dmrc

I get a message that $HOME/.dmrc does not exist

is there any other solutions one might have?

thanks

---

### Post by taurus on 2007-05-06
> **cbrad said:**
> I have tried all the chown and chmod ways and still am unable to log into ubuntu 7.04

one of the lines I have tried is 

chown -R username $HOME/.dmrc
chmod 644 $HOME/.dmrc

I get a message that $HOME/.dmrc does not exist

is there any other solutions one might have?

thanks

Why don't you replace $HOME with your actual login name.  Boot into recovery mode from GRUB and do

```
chmod 644 /home/brad/.dmrc
chown brad:brad /home/brad/.dmrc
```
assuming brad is your login name.

---

### Post by cbrad on 2007-05-06
Thank you for your reply

I still get the same message

I tried adding a new user after logging into the recover system

I entered

adduser ausername
At first, it seemed to wok; adding group, user name, directory, etc. Afterwards, a error message saying that symlink permission denied.

would it be possible to add a new user in the recovery and then log in the usual way?

---

### Post by taurus on 2007-05-06
What's the output of this command then?

```
ls -la /home
```

---

### Post by Devius on 2007-05-07
I got this once... I think the chmod is 755 and not 644. If you got nothing to loose try it and report back.

---

### Post by blargh on 2007-05-07
Hello,

I also get the "$HOME/.dmrc file has incorrect permissions and is being ignored. ... file sould be owned by user and have 644 permissions" dialog box error, when I log in.
But if I click in the "OK" button, I am logged in to GNOME (Ubuntu 7.04), instead of default KDE.
I tried:
[PHP]chmod 644 /home/my_user_name/.dmrc
chown my_user_name:my_user_name /home/my_user_name/.dmrc[/PHP]
but I get the same error when I log in.

The output to the "ls -la /home" command is:
[PHP]total 28
drwxr-xr-x  4 root root  4096 2007-04-29 01:45 .
drwxr-xr-x 21 root root  4096 2007-04-20 03:37 ..
lrwxrwxrwx  1 root root    44 2007-04-29 01:45 .directory -> /etc/kubuntu-default-settings/directory-home
drwx------  2 root root 16384 2007-04-20 03:26 lost+found
drwxrwxr-x 57 pp   pp    4096 2007-05-08 00:46 pp[/PHP]

I am using Ubuntu for 3 weeks and never tried Linux before: I have no idea what is happening or what can I do! Thank you for your time.

---

### Post by taurus on 2007-05-07
Is your login name **[COLOR="Blue"]pp[/COLOR]**?

```
ls -la /home/pp
```

---

### Post by mailbox on 2007-05-07
I'm having the exact same problem, but I don't have a ~/.dmrc file at all.

---

### Post by taurus on 2007-05-07
> **mailbox said:**
> I'm having the exact same problem, but I don't have a ~/.dmrc file at all.

```
ls -la ~
```

p.s.  If you don't have ~/.dmrc, a new one will be created it for you.

---

### Post by mailbox on 2007-05-07
-rw-r--r--   1 dissonance dissonance     24 2007-04-30 16:07 .dmrc


lemmie give it a shot.

---

### Post by mailbox on 2007-05-08
Nope, didn't work.

---

### Post by blargh on 2007-05-08
Hello Taurus, thank you for your help!

1 - Yes, my login name is pp;
2 - The reply to the command ls -la /home/pp is:
```
-rw-rw-r--  1 pp   pp          22 2007-04-29 14:52 .dmrc
```
3 - These  might help too:
```
drwxr-xr-x   4 root root  4096 2007-04-29 01:45 home
```
```
drwxrwxr-x 57 pp   pp    4096 2007-05-08 20:50 pp
```

Once again, thank you very much for your help!

---

### Post by blargh on 2007-05-08
Ignore this reply... sorry! I don't know how to delete it!!

---

### Post by taurus on 2007-05-08
I would make ~/.dmrc to be 644 instead of 664.

```
chmod 644 ~/.dmrc
ls -la ~/.dmrc
```

---

### Post by blargh on 2007-05-08
Did it, and the answer was:

-rw-r--r-- 1 pp pp 22 2007-04-29 14:52 .dmrc

But the problem remains the same!
Could it be a problem with the permissions of the /home and /pp directories? What are the "default" permissions for them?

---

### Post by taurus on 2007-05-08
What's the output of this command then?

```
ls -la /home
```

It should be

```
drwxr-xr-x 50 pp  pp  4096 2007-05-08 08:10  pp
```

---

### Post by blargh on 2007-05-08
The reply is
```
drwxr-xr-x  4 root root  4096 2007-04-29 01:45 .
drwxr-xr-x 21 root root  4096 2007-04-20 03:37 ..
lrwxrwxrwx  1 root root    44 2007-04-29 01:45 .directory -> /etc/kubuntu-default-settings/directory-home
drwx------  2 root root 16384 2007-04-20 03:26 lost+found
drwxrwxr-x 57 pp   pp    4096 2007-05-08 21:38 pp
```

Mmmm... There's an extra "w" in the last line.

---

### Post by taurus on 2007-05-08
```
cd /home
chmod 755 pp
ls -la
```

---

### Post by blargh on 2007-05-08
It worked :):  problem solved (for now). Meanwhile, I [red]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/33130") about other users with dual-boot having the same problem...

Thank you very much for your time and precious help, taurus!
I hope one day I can do the same for other ubuntu "newbies".
Thank you!

---

### Post by mailbox on 2007-05-09
> **taurus said:**
> ```
cd /home
chmod 755 pp
ls -la
```

this worked for me.
thanks, man!

---

### Post by ahildoer on 2007-05-11
Also, if you do not want others even having read access to your home directory, the following will solve the problem. Assuming your login is 'jdoe', do the following:

```

   
sudo chown jdoe:jdoe /home/jdoe
sudo chown jdoe:jdoe /home/jdoe/.dmrc
sudo chmod 750 /home/jdoe
sudo chmod 644 /home/jdoe/.dmrc
```

Keep in mind that you may be running some other application that requires read access on your home directory for everybody. Or, in more specific terms, there are some applications that require at least *chmod xx4* on your home directory (/home/jdoe in the code block above), rather than *chmod xx0*. I can't think of one off the top of my head, and I am even thinking of vmware server/workstation. But you may have one, so if something else breaks after you do this, that could be the explanation. But I _highly_ recommend my solution above at it is the most secure. 

-Anthony
[ahildoer@gmail.com]("mailto:ahildoer@gmail.com")
[http://www.hildoer.com]("http://www.hildoer.com")

---

### Post by wolterkabolter on 2007-05-11
I had the same problem and now my problem is even bigger...
I got the message that my file must have access 644. So I typed:

> cd /home
chmod 644 wolterkabolter
ls -la

And now I get the message that access has denied because he could not create /home/wolterkabolter/.gnome2. So I am in a save modus now, but I can' t get in to ubuntu anymoren. What should I do???

---

### Post by taurus on 2007-05-11
```

cd /home
sudo chmod 744 wolterkabolter
ls -la

```

---

### Post by Lucifiel on 2007-05-12
> **taurus said:**
> ```
cd /home
chmod 755 pp
ls -la
```

Woohoo that did wonders for me!!!!

Btw, users might want to try this instead. :p :

> sudo chmod -Rvf 755 <your user name>

---

### Post by ahildoer on 2007-06-17
This is not a good suggestion. It will allow EVERYONE on the system to be able to read EVERYTHING in your ENTIRE home directory. Do not do it unless you are OK with that. 

> **Lucifiel said:**
> Woohoo that did wonders for me!!!!

Btw, users might want to try this instead. :p :

```
sudo chmod -Rvf 755 <your user name>
```


---

### Post by ahildoer on 2007-06-17
> **wolterkabolter said:**
> I had the same problem and now my problem is even bigger...
I got the message that my file must have access 644. So I typed:

```

cd /home
chmod 644 wolterkabolter
ls -la
```

And now I get the message that access has denied because he could not create /home/wolterkabolter/.gnome2. So I am in a save modus now, but I can' t get in to ubuntu anymoren. What should I do???

The reason you got access denied was because you denied the user execute access on your home directory. Directories are not accessible without execute access. Also, that command you did only effected your home directory, not anything inside it. In other words, the command was not recursive. You needed to do the following:

```
sudo chmod 644 /home/wolterkabolter/.dmrc
```

This would have set the permissions on the .dmrc file, as the error message indicates should be done.

---

### Post by dhughes on 2007-07-28
> **ahildoer said:**
> Also, if you do not want others even having read access to your home directory, the following will solve the problem. Assuming your login is 'jdoe', do the following:

```

   
sudo chown jdoe:jdoe /home/jdoe
sudo chown jdoe:jdoe /home/jdoe/.dmrc
sudo chmod 750 /home/jdoe
sudo chmod 644 /home/jdoe/.dmrc
```

Keep in mind that you may be running some other application that requires read access on your home directory for everybody. Or, in more specific terms, there are some applications that require at least *chmod xx4* on your home directory (/home/jdoe in the code block above), rather than *chmod xx0*. I can't think of one off the top of my head, and I am even thinking of vmware server/workstation. But you may have one, so if something else breaks after you do this, that could be the explanation. But I _highly_ recommend my solution above at it is the most secure. 

-Anthony
[ahildoer@gmail.com]("mailto:ahildoer@gmail.com")
[http://www.hildoer.com]("http://www.hildoer.com")

 This comment by ahildoer should be stickied.

 I think this is what people are trying to do but only do half of it, or get chmod and chown mixed up, then they log out, can't get back in seeing the "$HOME/.dmrc" error message and then don't know what happened.

  The above solution would help a lot of people.

 Thanks ahildoer!

 **edit:** After looking and trying the above I think this should also be added.
 
 sudo chown jdoe:jdoe /home/jdoe/*   <-- note the asterisk

 and also

sudo chmod 750 /home/jdoe/*  <--- same again

 I think if you leave out the asterisk then you are only altering the directories and not the files within them. I'm not 100% sure about that but to me it seemed as if anything in the directory was not affected until then asterisk  * was added.

---

### Post by ahildoer on 2007-11-16
> **dhughes said:**
> 
 
 sudo chown jdoe:jdoe /home/jdoe/*   <-- note the asterisk

 and also

sudo chmod 750 /home/jdoe/*  <--- same again

 I think if you leave out the asterisk then you are only altering the directories and not the files within them. I'm not 100% sure about that but to me it seemed as if anything in the directory was not affected until then asterisk  * was added.

Adding the asterisk will chown and chmod the files INSIDE /home/jdoe, but NOT /home/jdoe itself. I recommend only changing the permissions on the home directory (non-recursively). If the directory permissions are correctly set, other users on the system can not freely browse your home directory. Also, directories and regular files require different permissions to function. Directories require execute permissions for a user to traverse or otherwise access files inside it, and they require write privileges for a user to delete, rename, or add file/directories within it. Files need only read access to view, and read/write access to edit. Files only need execute if they are scripts or executables. It does not make sense for a configuration file or an image file to have execute set. 

I hope this adds additional clarity.

---

### Post by ahildoer on 2007-12-02
Fix this problem and secure your home directory with this script. ***READ THE MAN SECTION IN SOURCE CODE***

How to Download, Install and Run:

```
wget http://www.hildoersystems.com/linux/scripts/setHomePermissions.pl
chmod 750 setHomePermissions.pl
./setHomePermissions.pl
```

Source code as of version  1.21_Alpha:

```
#!/usr/bin/perl
#####################################################################################
#
# Usage:
#
# 	setHomePermissions.pl 
#
# Command Description: 
#
# 	This command is used to recursively set file and directory permissions, and umasks on the user's
#	home directory. The permissions and ownership that it will set are the most secure possible, 
#	allowing access to a user's home directory only by the user and no one else. No one other than
#	the user will even have read access to the user's home directory. Also, umasks are set in 
#	order to ensure that newly created files and directories have the correct permissions by default.
#
#	This command will determine the location of a user's home directory from the value of 
#	the ~ system variable, and it will chown files with the username output from the whoami system 
#	command.
#
#	Chown commands are called sudo to ensure that that permissions and ownership on ALL files
#	and subdirectories in the user's homefolder are set to that user. This means that the user running
#	this command must be in the visudo file, wheel group or admin group as appropriate for your distro.
#
#	This command also sets the correct permissions and ownership on all .dmrc files according to
#	Gnome requirements.
#
#	Permissions on the .ssh directory and files contained there in are set to 700 and 600 respectively.
#
#	Symbolic Links - Since permissions are set with sudo, this command will not follow symbolic links. 	
#
# Delegation:
#
#	To allow another user read-only access to your home folder and all subdirectories, add them to your
#	group with the following command:
#
#			usermod -a -G [YOUR_USERNAME] [THEIR_USERNAME]
#
#	On their next log in, they will be able to read and execute any files in your home directory, as well
#	as any files anywhere in the system for which the group owner is your group.
#
# Permissions/Ownerships Set:
#
#	Directories: umask 027, chown USERAME:USERNAME, chmod 770
#	Executable Files: chown USERAME:USERNAME, chmod 750
#	Files: chown USERAME:USERNAME, chmod 640
#	.dmrc file: chown USERNAME:USERNAME, chmod 644
#
#	*IMPORTANT* USERNAME is determined with the whoami command. Thus, you must
#	run this command with the user who should own the home directory.
#
# Case Examples:
# 	
#	-All files with any existing permissions and named .dmrc will be changed to 644.
# 	-Files with permisions 700 will be changed to 750.
# 	-Files with permissons 777 will be changed to 750.
# 	-Files with permissons 000 will be changed to 640.
# 	-Files with permissons 067 will be changed to 640.
# 	-Files with permissons 060 will be changed to 640.
# 	-Files with permissons 660 will be changed to 640.
# 	-Files with permissons 070 will be changed to 640.
# 	-Files in the ~/.ssh directory with any permission will be changed to 600.
# 	-The directory .ssh with permission 777 will be changed to 700.
# 	-Directories with permissons 000 will be changed to 750.
# 	-Directories with permissons 777 will be changed to 750.
# 	-Directories with permissons 067 will be changed to 750.
# 	-Directories with permissons 060 will be changed to 750.
# 	-Directories with permissons 660 will be changed to 750.
# 	-Directories with permissons 070 will be changed to 750.
# 	-Directories with permissons 007 will be changed to 750.
# 	-Directories with permissons 700 will be changed to 750.
#
# Elevated Priviledges
#
# 	In order to perform chowning, the user running this command must have sudo access.
#
# Support:
#
# 	If you have trouble with this script, please contact:
# 			Anthony Hildoer <ahildoer@gmail.com>
#
# Versions:
#
#	1.21_Alpha - 20071203 - Fixed .ssh directory handling.
#	1.2_Alpha - 20071203 - Added support for .ssh directory, which needs to be more restrictive.
#			- Dropped some of the print statments to increase performance.
#	1.1_Alpha - 20071202 - Added support for .dmrc permissions according to Gnome requirements.
#			- Added automatic homedirectory locating by caching the value of ~ from the shell.
#			- Refactored source code organization.
# 	1.0_Alpha - 20070907 - Initial release.
#
# Copyright:
#
# 	Hildoer Systems 2007 : http://www.hildoersystems.com
#
# Warranty:
# 	
# 	This product in no way comes with a warranty. Any use is strictly at your
# 	own risk. If you have any concern regarding program behaviors, please feel
# 	free to contact the developer. See "Support" for contact information. Responses
# 	from or suggestions from the developer do not imply any warranty. Usage of this 
# 	script remains at your own risk.
# 
# Notes on Code:
# 	
# 	As you may notice, the code structure here is a bit over complicated for use
# 	of chmod and chown. Namely, the code handles recursions rather than calling 
# 	-R on both chmod and chown. This structure is intential in order to support
# 	additions to this script that may use commands that do not support recursion
# 	or that have poor support for recursion.
#
#####################################################################################

use strict;
use warnings;

my $index = 0;
my $whoami = `whoami`;
my $start = `echo ~`;

# clear newlines at end of values
$whoami =~ s/\n$//;
$start =~ s/\n$//;

if ($whoami =~ /^root$/) {
        print "Do not run this command as root.\n";
        exit 0;
}

if ( -d $start ) {

	# cache current directory.
	my $pwd = `pwd`;

	# remove trailing newline.
	$pwd =~ s/\n/g/;

	# set permissions on .ssh directory first, because it is most important!
	processSSH($start, $whoami);
	
	# start processing home directory and subdirectories.
	processDirectory($start, $pwd, $whoami, "");

	print "Done.\n";

} elsif ( -f $start ) {

	print "'$start' is not a directory.\n";

}

exit 0;

# subroutines

# check contents of $directory, process any directories contained therein. 
sub processDirectory {

	my ($directory, $returnDirectory, $whoami, $indent) = @_;

        my $dirHandle;
	my $file;
	my @directories;

	# symbolic links are not followed because if they link out of the home
	# directory, we do not want to set their permissions. If the link is to
	# another spot in the home directory, the contents will still get set
	# when the script gets to the directory which is linked to.
	if (-l $directory) {
		#print $indent."Skipping symbolic link $directory\n";
		return 0;
	} else {
		print $indent."Processing directory: $directory\n";
		$indent .= "\t";
	}

	# sets permissions on directory before trying to enter and change its contents.
	processFile($directory, $whoami, $indent);

	# enter directory and continue processing contents.
	if (chdir($directory)) {

		# set the permission mask for the current directory
		umask 027;

		# dirHandle allows access to filenames
		opendir($dirHandle, ".");
	
		# iterate through contents of the directory
       		foreach $file (sort readdir($dirHandle)) {

			# do not process the . and .. relative directory references
			if ( $file !~ /^\.$/ && $file !~ /^\.\.$/ ) {

				# if file is a directory, process it's contents.
				if ( -d $file && $file !~ /\/.ssh$/) {
					processDirectory($directory."/".$file, $directory, $whoami, $indent);
				} elsif (-f $file) {
					# sets permissions on files
					processFile($file, $whoami, $indent);
				}

			}

		}

		# exit this directory
		chdir($returnDirectory);

	} else {

		print $indent."Could not open directory: $directory. Skipping.\n";

	}
}

# set ownership and permissions on files/directories.
sub processSSH {

	my ($directory) = @_;

	print "Setting Permissions on .ssh Directory\n";
	
	print `sudo chmod -R 600 "$directory/.ssh" 2>&1`;
	print `sudo chmod 700 "$directory/.ssh" 2>&1`;

	return 0;
}

# set ownership and permissions on files/directories.
sub processFile {

	my ($file, $whoami, $indent) = @_;

	# this function also sets permissions on directories, but the
	# processDirectory function handles user updates for directories.
	if (-f $file) {
		# update the user on what is going on
		#print $indent."Processing file: $file\n";
	}

	# escape possible double quotes in filename
	$file =~ s/"/\\"/g;

	# set ownership
	print `sudo chown $whoami:$whoami "$file" 2>&1`;

	# owner gets rwx on directories and rw on files, plus x on files that are already executable.
	print `sudo chmod u+rwX "$file" 2>&1`;

	# group gets r-x on directories and r- on files, plus x on files that are already executable.
	print `sudo chmod g+rX "$file" 2>&1`;
	print `sudo chmod g-w "$file" 2>&1`;

	# others get --- on everything.
	print `sudo chmod o-rwx "$file" 2>&1`;

	# sets correct permissions on all .dmrc files. 
	if ($file =~ /^.dmrc$/) {
		print `sudo chmod 644 "$file" 2>&1`;
	}

}
```

Suggestions welcome.

---

### Post by BrentNewland on 2008-01-22
That script works perfectly! Would be better if it fixed ALL in the /home directory, perhaps by using the folder name to look up the user and make sure it matches, then use the user name to find the group it should be in and auto fix all.

I think it should be included in the official distro to auto fix directory permissions when GSM detects a permissions problem (instead of saying "Can't access ~./dmrc or lock .ICEauthority, go screw yourself" it could say "Warning: File privileges in /home/*username*/ have been changed. Would you like to auto-correct this problem?"

---

### Post by LeslieL on 2008-02-18
Just want to say thanks to everyone who contributed to this thread. It's helped me a lot. Thanks for sharing your experiences and knowledge.

---

### Post by dondad on 2008-02-18
Try this:

To fix file permissions after copying (works on home directory also DAMHIKT)

Navigate to the top file that you want to change along with everything below,

sudo chown -R user:user .

[COLOR="Red"]Note the dot[/COLOR]

then 

sudo chmod -R u_rwx .

[COLOR="red"]again, note the dot.[/COLOR]

(replace user with your username)

---

