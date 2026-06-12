---
title: "running a perl script"
date: 2007-08-09
forum: General Help
---

### Post by Alcopops on 2007-08-09
Hi all,

should it be possible to run a perl script from the terminal with a command like

/home/ubuntu/Desktop/prenominalNZB-0.1.tar.gz_FILES/prenominalNZB.pl

nothing seems to happen when I do.

However,

If i enter 

cd /home/ubuntu/Desktop/prenominalNZB-0.1.tar.gz_FILES

then enter

./prenominalNZB.pl

the script runs fine.

What do you think is  happening here?

I would like to run the script via cron and although i can write a bash script that changes directory then calls the perl script and just run this with cron, it seems like an inelegant way to go about it.

Any advice?

Cheers,

Jaime

---

### Post by apetresc on 2007-08-09
Those two calls should be absolutely identical. The "." in "./prenominalNZB.pl" just means "the current directory", so they expand to the same thing.

What does the script file do? It could be that the actions of the script itself are dependent on the pwd (current working directory), in which case it is running both times, just doing nothing in the former case.

Try adding a ```
print "Hello"
``` as the first line and see if it gets printed.

---

### Post by stchman on 2007-08-09
> **Alcopops said:**
> Hi all,

should it be possible to run a perl script from the terminal with a command like

/home/ubuntu/Desktop/prenominalNZB-0.1.tar.gz_FILES/prenominalNZB.pl

nothing seems to happen when I do.

However,

If i enter 

cd /home/ubuntu/Desktop/prenominalNZB-0.1.tar.gz_FILES

then enter

./prenominalNZB.pl

the script runs fine.

What do you think is  happening here?

I would like to run the script via cron and although i can write a bash script that changes directory then calls the perl script and just run this with cron, it seems like an inelegant way to go about it.

Any advice?

Cheers,

Jaime

Make sure your first line of the script is:

#!/usr/bin/perl

Then it will run.

---

### Post by apetresc on 2007-08-09
> **stchman said:**
> Make sure your first line of the script is:

#!/usr/bin/perl

Then it will run.
She said that she *can* run it with "./scriptname.pl" which wouldn't be possible unless #!/usr/bin/perl was already the first line of the script.

---

### Post by tomrules345 on 2007-08-09
Try running the command:

```
perl /home/ubuntu/Desktop/prenominalNZB.pl
```

This should work.

---

### Post by Alcopops on 2007-08-09
yep

#!/usr/bin/perl is there and # is the first character in the script.

I hadn't thought about the script contents being directory dependant, it's not my script and I don't know much (read: anything) about perl. I have included the script below so that others can give their opinion. Looking at it i seems to me that the path to the config file mentioned at the start of the script may need to be absolute. Any thoughts.

Thanks for all the help so far everyone.

ps sorry for the duplicate post below - don't know how it happened, don't know how to delete it. :-(

-----------------------------------------------------------------------------
#!/usr/bin/perl 
no strict 'refs';
use LWP::Simple;
use LWP::UserAgent;

sub read_config {
	open (CONFIG, "prenominalNZB.config");
	while (<CONFIG>) {
    		chomp;                  # no newline
        	s/#.*//;                # no comments
	    	s/^\s+//;               # no leading white
	        s/\s+$//;               # no trailing white
	   	next unless length;     # anything left?
			my ($var, $value) = split(/\s*=\s*/, $_, 2);
			$$var = $value;
	} 
	close CONFIG;
}

sub get_show {
my ($show) = $_[0];
my @ret = "";
if ( $show ne "" )
  {
  my $site = get "http://www.tvrage.com/quickinfo.php?show=".$show;

  foreach $line (split("\n",$site) )
    {
    my ($sec,$val) = split('\@',$line,2);
    if ($sec eq "Show Name" )
      {
      $ret[0] = $val;
      }
    elsif ( $sec eq "Show URL" )
      {
      $ret[1] = $val;
      }
    elsif ( $sec eq "Premiered" )
      {
      $ret[2] = $val;
      }
    elsif ($sec eq "Country" )
      {
      $ret[7] = $val;
      }
    elsif ( $sec eq "Status" )
      {
      $ret[8] = $val;
      }
    elsif ( $sec eq "Classification" )
      {
      $ret[9] = $val;
      }
    elsif ( $sec eq "Genres" )
      {
      $ret[10] = $val;
      }
    elsif ( $sec eq "Network" )
      {
      $ret[11] = $val;
      }
    elsif ( $sec eq "Airtime" )
      {
      $ret[12] = $val;
      }
    elsif ( $sec eq "Latest Episode" )
      {
      my($ep,$title,$airdate) = split('\^',$val);
      $ret[3] = $ep.", \"".$title."\" aired on ".$airdate;
      }
    elsif ( $sec eq "Next Episode" )
      {
      my($ep,$title,$airdate) = split('\^',$val);
      $ret[4] = $ep.", \"".$title."\" airs on ".$airdate;
      }
    elsif ( $sec eq "Episode Info" )
      {
      my($ep,$title,$airdate) = split('\^',$val);
      $ret[5] = $ep.", \"".$title."\" aired on ".$airdate;
      }
    elsif ( $sec eq "Episode URL" )
      {
      $ret[6] = $val;
      }

    }
  if ( $ret[0] )
    {

    return @ret;
    }
  else
    {
    return 0;
    }
  }
return 0;
}


sub get_nzb {
	my ($nzbid) = $_[0];

	my $newzbin = LWP::UserAgent->new;
	$newzbin->agent("prenominalNZB/0.1b");

	my $req = HTTP::Request->new(POST => 'http://v3.newzbin.com/api/dnzb/');
	$req->content_type('application/x-www-form-urlencoded');
	$req->content('username='.$newzbin_username.'&password='.$newzbin_password.'&reportid='.$nzbid);
	

	my $res = $newzbin->request($req);

	 if ($res->is_success) {
	 	print "Retrieving NZB file from Newzbin\n";
	 	$filename = $res->header("X-DNZB-Name"); #retrieve the postname from the header
	 	open (NZB,">$nzb_queue$filename.nzb");	#save the filename to the queue
		print NZB $res->content;
		close NZB;
	 }
	else {
		print $res->status_line, "\n";
    		if ($res->status_line =~ /^400.*/) {
			print "Error 400: Bad request invalid parameters\n";
		} elsif ($res->status_line =~ /^401.*/) {
			print "Error 401: username or password invalid\n";
		} elsif ($res->status_line =~ /^402.*/) {
			print "Error 402: Payment required\n";
		} elsif ($res->status_line =~ /^404.*/) {
			print "Error 404: Data not found\n";
		} elsif ($res->status_line =~ /^450.*/) {
			print "Error 450: too many requests, please wait\n";
		} elsif ($res->status_line =~ /^500.*/) {
			print "Error 500: Internal server error\n";
		} elsif ($res->status_line =~ /^503.*/) {
			print "Error 503: Service unavailable, site is down\n";
		}

	}

return 0;
}

sub get_series 
{
	open (SERIES,"prenominalNZB.series");
	open (SERIESNEW,">prenominalNZB.series.new");
	while (<SERIES>)
		{	
			$orgline = $_;
			if (/^#.*/)  { print SERIESNEW $orgline; next }
			chomp;
			my ($serie,$DWNlast) = split('\|',$_);
			@show_info = &get_show($serie);
			print "Show: \t\t@show_info[0] \n";
			print "Latest episode: @show_info[3] \n";
			print "next episode: \t@show_info[4] \n";
			print "Status: \t@show_info[8] \n";

			my ($AIRlast,$episodetitle) = split (',',@show_info[3],0);
			($AIRseasson,$AIRepisode) = split ('x', $AIRlast);
			($DWNseasson,$DWNepisode) = split ('x', $DWNlast);

			if ( (($DWNseasson == $AIRseasson) && ( $DWNepisode < $AIRepisode )) || (($DWNseasson < $AIRseasson) && ($DWNepisode > $AIRepisode)) )
				{
					print "New Episode found\n";
					$AIRseasson =~ s/^0//;
					$episodetitle =~ s/^ "//;
					$episodetitle =~ s/".*//;
					$nzbid = search_nzb(@show_info[0] ,$AIRseasson."x".$AIRepisode,$episodetitle);
					if ( $nzbid ne 0 ) {
						get_nzb($nzbid);
						print SERIESNEW "$serie|".$AIRseasson."x".$AIRepisode."\n";
					}
				} else {
					print "Latest episode allready downloaded\n";
					print SERIESNEW $orgline;
				}
			print "\n";
		}
		close SERIES;
		close SERIESNEW;
		system ("mv prenominalNZB.series.new prenominalNZB.series");
}

sub search_nzb {
	my ($show) = $_[0];
	my ($episode) = $_[1];
	my ($episodetitle) = $_[2];

	$newzbin_query = "?q=$show+$episode+$episodetitle";
	$newzbin_query .= "&searchaction=Search";
	$newzbin_query .= "&fpn=p";
	$newzbin_query .= "&category=8";
	$newzbin_query .= "&area=-1";
	$newzbin_query .= "&u_nfo_posts_only=0";
	$newzbin_query .= "&u_url_posts_only=0";
	$newzbin_query .= "&u_comment_posts_only=0";
	$newzbin_query .= "&u_v3_retention=".$nzb_retention * 24 * 60 * 60;
	$newzbin_query .= "&ps_rb_language=$LANG_English";
	$newzbin_query .= "&sort=ps_edit_date";
	$newzbin_query .= "&order=desc";
	$newzbin_query .= "&areadone=-1";
	$newzbin_query .= "&feed=csv";
	$newzbin_query .= "&ps_rb_video_format=21";
	
	my $newzbin = LWP::UserAgent->new;
	$newzbin->agent("prenominalNZB/0.1b");

	my $req = HTTP::Request->new(GET => 'http://v3.newzbin.com/search/'.$newzbin_query);

	my $res = $newzbin->request($req);

	 if ($res->is_success) {
		($date,$date2,$nzbid,$nzbtitle,$nzburl,$tvurl,$nzbNG) = split (",",$res->content);
		$nzbid =~ s/"//g;
		return $nzbid;
	 }
	else {
		print $res->status_line, "\n";
		return 0;
	}
}



{
read_config;
($show, $seasson, $episode) = get_series;
}

---

### Post by Alcopops on 2007-08-09
yep

#!/usr/bin/perl is there and # is the first character in the script.

I hadn't thought about the script contents being directory dependant, it's not my script and I don't know much (read: anything) about perl. I have included the script below so that others can give their opinion. Looking at it, it seems to me that the path to the config file mentioned at the start of the script may need to be absolute. Any thoughts.

Thanks for all the help so far everyone.

-----------------------------------------------------------------------------
#!/usr/bin/perl 
no strict 'refs';
use LWP::Simple;
use LWP::UserAgent;

sub read_config {
	open (CONFIG, "prenominalNZB.config");
	while (<CONFIG>) {
    		chomp;                  # no newline
        	s/#.*//;                # no comments
	    	s/^\s+//;               # no leading white
	        s/\s+$//;               # no trailing white
	   	next unless length;     # anything left?
			my ($var, $value) = split(/\s*=\s*/, $_, 2);
			$$var = $value;
	} 
	close CONFIG;
}

sub get_show {
my ($show) = $_[0];
my @ret = "";
if ( $show ne "" )
  {
  my $site = get "http://www.tvrage.com/quickinfo.php?show=".$show;

  foreach $line (split("\n",$site) )
    {
    my ($sec,$val) = split('\@',$line,2);
    if ($sec eq "Show Name" )
      {
      $ret[0] = $val;
      }
    elsif ( $sec eq "Show URL" )
      {
      $ret[1] = $val;
      }
    elsif ( $sec eq "Premiered" )
      {
      $ret[2] = $val;
      }
    elsif ($sec eq "Country" )
      {
      $ret[7] = $val;
      }
    elsif ( $sec eq "Status" )
      {
      $ret[8] = $val;
      }
    elsif ( $sec eq "Classification" )
      {
      $ret[9] = $val;
      }
    elsif ( $sec eq "Genres" )
      {
      $ret[10] = $val;
      }
    elsif ( $sec eq "Network" )
      {
      $ret[11] = $val;
      }
    elsif ( $sec eq "Airtime" )
      {
      $ret[12] = $val;
      }
    elsif ( $sec eq "Latest Episode" )
      {
      my($ep,$title,$airdate) = split('\^',$val);
      $ret[3] = $ep.", \"".$title."\" aired on ".$airdate;
      }
    elsif ( $sec eq "Next Episode" )
      {
      my($ep,$title,$airdate) = split('\^',$val);
      $ret[4] = $ep.", \"".$title."\" airs on ".$airdate;
      }
    elsif ( $sec eq "Episode Info" )
      {
      my($ep,$title,$airdate) = split('\^',$val);
      $ret[5] = $ep.", \"".$title."\" aired on ".$airdate;
      }
    elsif ( $sec eq "Episode URL" )
      {
      $ret[6] = $val;
      }

    }
  if ( $ret[0] )
    {

    return @ret;
    }
  else
    {
    return 0;
    }
  }
return 0;
}


sub get_nzb {
	my ($nzbid) = $_[0];

	my $newzbin = LWP::UserAgent->new;
	$newzbin->agent("prenominalNZB/0.1b");

	my $req = HTTP::Request->new(POST => 'http://v3.newzbin.com/api/dnzb/');
	$req->content_type('application/x-www-form-urlencoded');
	$req->content('username='.$newzbin_username.'&password='.$newzbin_password.'&reportid='.$nzbid);
	

	my $res = $newzbin->request($req);

	 if ($res->is_success) {
	 	print "Retrieving NZB file from Newzbin\n";
	 	$filename = $res->header("X-DNZB-Name"); #retrieve the postname from the header
	 	open (NZB,">$nzb_queue$filename.nzb");	#save the filename to the queue
		print NZB $res->content;
		close NZB;
	 }
	else {
		print $res->status_line, "\n";
    		if ($res->status_line =~ /^400.*/) {
			print "Error 400: Bad request invalid parameters\n";
		} elsif ($res->status_line =~ /^401.*/) {
			print "Error 401: username or password invalid\n";
		} elsif ($res->status_line =~ /^402.*/) {
			print "Error 402: Payment required\n";
		} elsif ($res->status_line =~ /^404.*/) {
			print "Error 404: Data not found\n";
		} elsif ($res->status_line =~ /^450.*/) {
			print "Error 450: too many requests, please wait\n";
		} elsif ($res->status_line =~ /^500.*/) {
			print "Error 500: Internal server error\n";
		} elsif ($res->status_line =~ /^503.*/) {
			print "Error 503: Service unavailable, site is down\n";
		}

	}

return 0;
}

sub get_series 
{
	open (SERIES,"prenominalNZB.series");
	open (SERIESNEW,">prenominalNZB.series.new");
	while (<SERIES>)
		{	
			$orgline = $_;
			if (/^#.*/)  { print SERIESNEW $orgline; next }
			chomp;
			my ($serie,$DWNlast) = split('\|',$_);
			@show_info = &get_show($serie);
			print "Show: \t\t@show_info[0] \n";
			print "Latest episode: @show_info[3] \n";
			print "next episode: \t@show_info[4] \n";
			print "Status: \t@show_info[8] \n";

			my ($AIRlast,$episodetitle) = split (',',@show_info[3],0);
			($AIRseasson,$AIRepisode) = split ('x', $AIRlast);
			($DWNseasson,$DWNepisode) = split ('x', $DWNlast);

			if ( (($DWNseasson == $AIRseasson) && ( $DWNepisode < $AIRepisode )) || (($DWNseasson < $AIRseasson) && ($DWNepisode > $AIRepisode)) )
				{
					print "New Episode found\n";
					$AIRseasson =~ s/^0//;
					$episodetitle =~ s/^ "//;
					$episodetitle =~ s/".*//;
					$nzbid = search_nzb(@show_info[0] ,$AIRseasson."x".$AIRepisode,$episodetitle);
					if ( $nzbid ne 0 ) {
						get_nzb($nzbid);
						print SERIESNEW "$serie|".$AIRseasson."x".$AIRepisode."\n";
					}
				} else {
					print "Latest episode allready downloaded\n";
					print SERIESNEW $orgline;
				}
			print "\n";
		}
		close SERIES;
		close SERIESNEW;
		system ("mv prenominalNZB.series.new prenominalNZB.series");
}

sub search_nzb {
	my ($show) = $_[0];
	my ($episode) = $_[1];
	my ($episodetitle) = $_[2];

	$newzbin_query = "?q=$show+$episode+$episodetitle";
	$newzbin_query .= "&searchaction=Search";
	$newzbin_query .= "&fpn=p";
	$newzbin_query .= "&category=8";
	$newzbin_query .= "&area=-1";
	$newzbin_query .= "&u_nfo_posts_only=0";
	$newzbin_query .= "&u_url_posts_only=0";
	$newzbin_query .= "&u_comment_posts_only=0";
	$newzbin_query .= "&u_v3_retention=".$nzb_retention * 24 * 60 * 60;
	$newzbin_query .= "&ps_rb_language=$LANG_English";
	$newzbin_query .= "&sort=ps_edit_date";
	$newzbin_query .= "&order=desc";
	$newzbin_query .= "&areadone=-1";
	$newzbin_query .= "&feed=csv";
	$newzbin_query .= "&ps_rb_video_format=21";
	
	my $newzbin = LWP::UserAgent->new;
	$newzbin->agent("prenominalNZB/0.1b");

	my $req = HTTP::Request->new(GET => 'http://v3.newzbin.com/search/'.$newzbin_query);

	my $res = $newzbin->request($req);

	 if ($res->is_success) {
		($date,$date2,$nzbid,$nzbtitle,$nzburl,$tvurl,$nzbNG) = split (",",$res->content);
		$nzbid =~ s/"//g;
		return $nzbid;
	 }
	else {
		print $res->status_line, "\n";
		return 0;
	}
}



{
read_config;
($show, $seasson, $episode) = get_series;
}

---

### Post by tomrules345 on 2007-08-09
Okie Dokie,

The Script run's fine for me when i try to use if from the current working directory and from the root directory, now im not sure what your problem is although it could just be me:D

---

### Post by apetresc on 2007-08-09
The method "read_config" has the line ```
open (CONFIG, "prenominalNZB.config");
``` which looks for the file "prenominalNZB.config" in the local directory. This is why it works when you're in the same dir, but not otherwise: it can't find the config file.

[quote=tomrules345]The Script run's fine for me when i try to use if from the current working directory and from the root directory, now im not sure what your problem is although it could just be me[/code]
Um, how? Unless you have the config file it shouldn't be running in either case...

---

