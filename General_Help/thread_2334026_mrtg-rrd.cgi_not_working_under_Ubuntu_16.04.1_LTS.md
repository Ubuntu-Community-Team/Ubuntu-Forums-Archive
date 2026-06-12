---
title: "mrtg-rrd.cgi not working under Ubuntu 16.04.1 LTS"
date: 2016-08-15
forum: General Help
---

### Post by sirdir on 2016-08-15
Hi!

I just upgraded from Ubuntu 14.04 LTS to 16.04 LTS. 
Not, the mrtg-rrd.cgi (from packet mrtg-rrd) is no longer working.
Comparing with the old version it seems just the 'defined' statement has been removed in various places, because that wouldn't work in Perl 5 version 22.

I don't know perl, but at least in one place I guess something must be wrong (it's a line where the defined has been removed:
[COLOR=#000000][FONT=Menlo][Mon Aug 15 22:57:28.088652 2016] [cgi:error] [pid 13319] [client 192.168.1.1:53513] AH01215: Can't use an undefined value as an ARRAY reference at /usr/lib/cgi-bin/mrtg-rrd.cgi line 911.: /usr/lib/cgi-bin/mrtg-rrd.cgi

Anyone similar problems, or better yet, a fix?

[/FONT][/COLOR]

---

### Post by sirdir on 2016-08-19
nobody?

---

### Post by deti on 2016-08-31
Same problem here.

---

### Post by deti on 2016-08-31
Fixed it:
--- /usr/lib/cgi-bin/mrtg-rrd.cgi	2015-08-02 13:20:11.000000000 +0200
+++ /usr/lib/cgi-bin/mrtg-rrd1.cgi	2016-08-31 11:21:19.540540237 +0200
@@ -496,7 +496,7 @@
 {
 	my ($name, $target, $q) = @_;
 
-	return @{$target->{args}} if @{$target->{args}};
+	return @{$target->{args}} if ($target->{args} && @{$target->{args}});
 
 	my $noi = 1 if $target->{options}{noi};
 	my $noo = 1 if $target->{options}{noo};
@@ -908,7 +908,7 @@
 	print $directories{$dir}{bodytag};
 
 	my $subdirs_printed;
-	if (@{$directories{$dir}{subdir}}) {
+	if ($directories{$dir}{subdir} && @{$directories{$dir}{subdir}}) {
 		$subdirs_printed = 1;
 		print <<EOF;
 <H1>MRTG subdirectories in the directory $dir1</H1>

---

