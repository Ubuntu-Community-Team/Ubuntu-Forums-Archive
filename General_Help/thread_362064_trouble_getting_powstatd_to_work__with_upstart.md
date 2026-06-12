---
title: "trouble getting powstatd to work  with upstart"
date: 2007-02-15
forum: General Help
---

### Post by urt99763urt on 2007-02-15
Hi, 

I'm have trouble getting powstatd working on edgy - or rather it appears that powstatd is working fine, but I can't get init to invoke /etc/init.d/powerfail  

I have powstatd  is running and it changes the values in /etc/powerstatus and sends a SIGPWR interrupt to init when the power to the UPS is cut. However after that nothing happens. 

The man pages for powstatd state that I should add the following lines to my inittab file
     
# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop
    
Unfortunately, since edgy has moved to using upstart there is no inittab file and it is unclear what I should do at this point.  Is there something that I can add to /etc/events.d/  that will handle this? 

Just for fun I searched through the sources of upstart-0.3.5 and sysvinit-2.86 in order to compare them. SIGPWR does not appear anywhere in the init for upstart whereas it does appear in the sysvinit code. 

Also I have had this UPS working with powstatd on this maching using debian sarge. 

Anyone have any ideas?

Thanks, Will

---

### Post by keybuk on 2007-02-15
What signals does powstatd use?

---

### Post by urt99763urt on 2007-02-15
Signals from the UPS to powstatd are sent via the serial port.

the output of powstatd -t  is as follows 

powstatd: online (standalone), watching /dev/ttyS0.
CTS DSR DCD RNG   DTR RTS   STATUS
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 0   0   1   0     0   1    FAIL
 0   0   1   0     0   1    FAIL
 0   0   1   0     0   1    FAIL
 0   0   1   0     0   1    FAIL
 0   0   1   0     0   1    FAIL
 0   0   1   0     0   1    FAIL
powstatd: power is failing.
 0   0   1   0     0   1    FAIL
 0   0   1   0     0   1    FAIL
 0   0   1   0     0   1    FAIL
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
powstatd: power restored.
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
 1   0   1   0     0   1    OK
  
You can see where I pulled the plug (cut power) to the UPS when CTS goes to 0 and DTR says FAIL.  

My powstatd.conf file is as follows

# Sample configuration file; appropriate for Cyber Power Systems Power99,
# Power2000 and PowerSL UPSes.

# Watch /dev/ttyS0
watch ttyS0

# CTS goes low when mains fail.
fail cts 0
# DCD goes low when battery is too low.
low dcd 0

# RTS must be set high at initialization.
init rts 1

# DTR is initially set low; pulling it high causes UPS to turn off if main
# power is gone.
init dtr 0
kill dtr 1

I've checked this config file with the old one from my working setup on debian sarge and it is the  same. So I think this configuration is correct. Note, this is the same UPS and computer. 
The main difference is that the debian installation used the sysvinit whereas ubuntu uses upstart.  

Also I'm pretty sure powstatd is working. When powstatd is running and I cut the power to the
UPS the value in /etc/powerstatus changes form OK to FAIL. Presumably at this time (according the the man pages) powstatd is also sends a SIGPWR singal to init. Init is then suppose to check 
/etc/powerstatus to see if it contains "OK",  "FAIL" or "LOW".  I'm pretty sure that this is the step 
where things are going wrong.   How can I check that init is getting the SIGPWR interrupt?
Also using the new upstart init how can I get init to respond to this signal based on the values in /etc/powerstatus?

On my old debian setup I had the following lines in inittab

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

Basically I need a way to do the same thing with the new upstart init program, but I'm not sure how to proceed.  

From looking at the source code for the upstart init it doesn't look like it has any code to respond to the SIGPWR interrupt. I could be wrong here, but it looks like the new init is not going to work with a lot of the UPS daemons (genpower, upsd, powstatd) which all work in the same manner).  I hope I'm wrong. 

Thanks, 
Will

---

### Post by urt99763urt on 2007-02-15
Ok, I looked a into this a little more deeply and I think this might be a
problem with the upstart init not handling the SIGPWR interrupt.
Whereas the sysvinit (2.86) init does handle the SIGPWR
interrupt. Basically I think this means that many of the UPS daemons
might be broken on ubuntu edgy under upstart. Unless there is some
compatability layer that I'missing or maybe I don't understand what
I'm looking at ...


The SIGPWR signal from powstatd is sent to init as follows (this is
from powstatd.c main)

	    
	    ...

	  /* Next write appropriate status indicator to status file
	   * (usually /etc/powerstatus) and then signal init. Note
	   * that init must already know where to look! Also, if you
	   * are running in test mode, don't actually signal init. */
	  if (!testMode)
	    {
	      sfp = fopen (sfile, "w");
	      fprintf (sfp, "%s", PSHOW (newStatus));
	      fclose (sfp);
	      kill (1, SIGPWR);
	    }

	    ...
 

code from init.c in sysvinit-2.86 for handling SIGPWR is shown here


void process_signals()
{
  CHILD		*ch;
  int		pwrstat;
  int		oldlevel;
  int		fd;
  char		c;

  if (ISMEMBER(got_signals, SIGPWR)) {
	INITDBG(L_VB, "got SIGPWR");
	/* See _what_ kind of SIGPWR this is. */
	pwrstat = 0;
	if ((fd = open(PWRSTAT, O_RDONLY)) >= 0) {
		c = 0;
		read(fd, &c, 1);
		pwrstat = c;
		close(fd);
		unlink(PWRSTAT);
	}
	do_power_fail(pwrstat);
	DELSET(got_signals, SIGPWR);
  }

  ....


Note, PWRSTAT is set to "/etc/powerstatus"
 
The do_power_fail function is as follows 


void do_power_fail(int pwrstat)
{
	CHILD *ch;

	/*
	 *	Tell powerwait & powerfail entries to start up
	 */
	for (ch = family; ch; ch = ch->next) {
		if (pwrstat == 'O') {
			/*
		 	 *	The power is OK again.
		 	 */
			if (ch->action == POWEROKWAIT)
				ch->flags &= ~XECUTED;
		} else if (pwrstat == 'L') {
			/*
			 *	Low battery, shut down now.
			 */
			if (ch->action == POWERFAILNOW)
				ch->flags &= ~XECUTED;
		} else {
			/*
			 *	Power is failing, shutdown imminent
			 */
			if (ch->action == POWERFAIL || ch->action == POWERWAIT)
				ch->flags &= ~XECUTED;
		}
	}
}

you can see where the powerokwait, powerfailnow, powerfail actions are set. 


Unfortunately there doesn't seem be be any equivalent code in the
upstart init. grepping through the sources of upstart-0.3.5 I could
only find one instance of SIGPWR in /nih/signals.c, but there are no
handlers for SIGPWR in the upstart init that I could find. As far as I
can see upstart init ignores the SIGPWR interupt.

I think I'm going to inquire about this on the upstart-devel mailing
list. Maybe I'm missing something ... very possible. 

Thanks, 
Will

---

### Post by urt99763urt on 2007-02-16
Hi, just an update. I received the following response from Scott Remnant on the upstart-devel
mailing list.   It includes a patch to init/main.c  as well as a update to the /etc/powerfail file. 
I haven't had a chance to test it yet. I think the patch is for upstart-0.3.5 and I'm currently running edgy which runs upstart-0.2.7-7. There have been some changes in upstart from versions 0.2.7 to 0.3.5. I think feisty is running 0.3.5 so I might try it on a spare box to test the patch.  I've attached the patch if anyone else is interested. I think a similar patch could be made for upstart 0.2.7. 

> On Thu, 2007-02-15 at 18:04 -0800, Will Dickson wrote:

> > Hi, I've been trying to get  powstatd to work with the upstart init 
> > program on ubuntu edgy and have been having some difficulties. I 
> > verified that powstatd is performing correctly - i.e.,  when the power 
> > to the UPS is cut powstatd changes the entry in /etc/powerstatus from OK 
> > to FAIL and sends a SIGPWR interrupt to init. Init is then suppose to 
> > check the entry in /etc/powerstatus etc. However, I couldn't seem to get 
> > the upstart init to respond to the SIGPWR interrupt.
> > 
> Right, I never included the SIGPWR code in init because I didn't know
> whether it was still used or not.

> > I grepped around in the upstart-0.3.5 sources and couldn't find any 
> > handlers for SIGPWR. Whereas the sysvinit does have a handler for SIGPWR
> > Am I missing something? Is there a way to make the upstart init work 
> > with the UPS daemons?
> >
 
> The attached patch and job file should do the trick; after installing,
> you should be able to write jobs with:

>	start on power-status fail
>	start on power-status low
>	start on power-status ok

> in them.

> lease let me know whether this works, so I can commit it.


> In the longer term, powstatd should emit its own upstart events instead
> of sending a signal -- that provides for a lot more flexibility; e.g.
> you could emit a "power-level" event every time the battery charge
> decreased by 5%, etc.

> Scott
> -- Have you ever, ever felt like this? Had strange things happen? Are you going round the 
> twist?

init/main.c patch 
-----------------------------------------------------------------------------------------------------------------------
=== modified file 'ChangeLog'
--- ChangeLog	2007-02-13 15:53:39 +0000
+++ ChangeLog	2007-02-16 10:20:21 +0000
@@ -1,3 +1,9 @@
+2007-02-16  Scott James Remnant  <scott@netsplit.com>
+
+	* init/main.c (pwd_handler): Handle the SIGPWR signal by generating
+	the new event.
+	* init/event.h (PWRSTATUS_EVENT): Add new generated event.
+
 2007-02-13  Scott James Remnant  <scott@netsplit.com>
 
 	* upstart/tests/test_message.c (test_reader, test_handle_using)

=== modified file 'init/event.h'
--- init/event.h	2007-02-09 19:39:42 +0000
+++ init/event.h	2007-02-16 10:13:42 +0000
@@ -123,6 +123,14 @@
  **/
 #define KBDREQUEST_EVENT "kbdrequest"
 
+/**
+ * PWRSTATUS_EVENT:
+ *
+ * Name of the event that we generate when we receive SIGPWR, indicating
+ * that the power status has changed.
+ **/
+#define PWRSTATUS_EVENT "power-status-changed"
+
 
 /**
  * JOB_STARTING_EVENT:

=== modified file 'init/main.c'
--- init/main.c	2007-02-09 21:16:28 +0000
+++ init/main.c	2007-02-16 10:20:12 +0000
@@ -65,6 +65,7 @@
 static void crash_handler   (int signum);
 static void cad_handler     (void *data, NihSignal *signal);
 static void kbd_handler     (void *data, NihSignal *signal);
+static void pwr_handler     (void *data, NihSignal *signal);
 static void stop_handler    (void *data, NihSignal *signal);
 static void term_handler    (const char *prog, NihSignal *signal);
 
@@ -214,6 +215,7 @@
 	nih_signal_set_handler (SIGTERM,  nih_signal_handler);
 	nih_signal_set_handler (SIGINT,   nih_signal_handler);
 	nih_signal_set_handler (SIGWINCH, nih_signal_handler);
+	nih_signal_set_handler (SIGPWR,   nih_signal_handler);
 	nih_signal_set_handler (SIGSEGV,  crash_handler);
 	nih_signal_set_handler (SIGABRT,  crash_handler);
 
@@ -234,6 +236,9 @@
 		NIH_MUST (nih_signal_add_handler (NULL, SIGWINCH,
 						  kbd_handler, NULL));
 
+	/* powstatd sends us SIGPWR when it changes /etc/powerstatus */
+	NIH_MUST (nih_signal_add_handler (NULL, SIGPWR, pwr_handler, NULL));
+
 	/* SIGTERM instructs us to re-exec ourselves */
 	NIH_MUST (nih_signal_add_handler (NULL, SIGTERM,
 					  (NihSignalHandler)term_handler,
@@ -412,6 +417,22 @@
 }
 
 /**
+ * pwd_handler:
+ * @data: unused,
+ * @signal: signal that called this handler.
+ *
+ * Handle having recieved the SIGPWR signal, sent to us when powstatd
+ * changes the /etc/powerstatus file.  We just generate a
+ * power-status-changed event and jobs read the file.
+ **/
+static void
+pwd_handler (void      *data,
+	     NihSignal *signal)
+{
+	event_emit (PWRSTATUS_EVENT, NULL, NULL);
+}
+
+/**
  * stop_handler:
  * @data: unused,
  * @signal: signal caught.
 



/etc/powerfail changes
-------------------------------------------------------------------------------------------------------------------------
description	"Handle changes to the /etc/powerstatus file"
author		"Scott James Remnant"

start on power-status-changed

script
	PWRSTATUS=$(cat /etc/powerstatus)

	if [ $PWRSTATUS = "OK" ]; then
		initctl emit power-status ok
	elif [ $PWRSTATUS = "FAIL" ]; then
		initctl emit power-status fail
	elif [ $PWRSTATUS = "LOW" ]; then
		initctl emit power-status low
	fi
end script

---

