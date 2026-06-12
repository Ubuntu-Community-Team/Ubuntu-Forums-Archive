---
title: "debmirror doesn't parse Package files anymore?"
date: 2005-08-29
forum: General Help
---

### Post by haraldkl on 2005-08-29
Hi i've set up a debmirror on my laptop, to get the Packages to Computers, that don't have a fast Internet connection. It perfectly worked until today.
Now I ran suddenly into the following Problem: debmirror does not seem to parse the package files properly. The parsing does not return any packages to be updated, even if my local pool directory is empty. Everything else in the script seems to work just perfectly fine...

Here is the code snippet from the Script that seems to cause the problems:
```
  foreach my $file (@package_files) {
    my $gunzf = gzopen($file, "rb") or die "$file: $!";
    my $line;
    my $res;
    my $loop = 1;
    while ($loop) {
      my $buf = "";
      while(($res = $gunzf->gzreadline($line) > 0)
	    && !($line =~ /^$/)) {
	$buf = $buf . $line;
      }
      if ($res <= 0) {
	$loop = 0;
	next;
      }
      $_ = $buf;
      ($filename)=m/^Filename:\s+(.*)/im;
      ($deb_section)=m/^Section:\s+(.*)/im;
      ($deb_priority)=m/^Priority:\s+(.*)/im;
      ($architecture)=m/^Architecture:\s+(.*)/im;
      next if (!$arches{$architecture});
      if(!(defined($include) && ($filename=~/$include/o))) {
	next if (defined($exclude) && $filename=~/$exclude/o);
	next if (defined($exclude_deb_section) && defined($deb_section)
		 && $deb_section=~/$exclude_deb_section/o);
	next if (defined($limit_priority) && defined($deb_priority)
		 && ! ($deb_priority=~/$limit_priority/o));
      }
      next if (exists $files{$filename}); # multiple occurences
      ($size)=m/^Size:\s+(\d+)/im;
      ($md5sum)=m/^MD5sum:\s+([A-Za-z0-9]+)/im;
      if (check_file($filename, $size, $md5sum)) {
	$files{$filename} = 1;
      } else {
	$files{$filename} = 0;
	$file_lists_md5{$filename} = $md5sum;
	$file_lists_size{$filename} = $size;
	$bytes_to_get += $size;
      }
    }
    $gunzf->gzclose();
  }
```

Especially this loop:
```
      
      while(($res = $gunzf->gzreadline($line) > 0)
	    && !($line =~ /^$/)) {
	$buf = $buf . $line;
      }
```

The loop seems never to leave because of an empty line, which is what it is supposed to do, i guess. I tried several mirrors, and they are all the same. grepping for those empty lines on the Packages files however suggests those empty lines are in the file.
I have near to no knowlege of Perl, and can't figure out this!
Does anybody else has a problem like that? Has anybody a suggestion, how to solve this?

Thanks a lot!

---

### Post by haraldkl on 2005-09-14
OK, I found my mistake.
During a system update of my Laptop I installed unthoughtfully a new version of Compress-Zlib (2.0), this is a development release, and I didn't have any intention to use it. So I should have paid more intention to the update.

It seems there has a major change from Version 1.38 to 2.0 in way, that debmirror can't handle. So debmirror doesn't work with Perl module Compress-Zlib-2.0. But as long as this is still a development release, I wouldn't put any effort in it, to make debmirror with the new release...

Sorry for bothering you with this totally unnecessary Problem  :???:

---

