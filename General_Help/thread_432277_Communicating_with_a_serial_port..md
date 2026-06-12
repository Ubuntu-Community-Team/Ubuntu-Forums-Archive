---
title: "Communicating with a serial port."
date: 2007-05-03
forum: General Help
---

### Post by musther on 2007-05-03
I have a device I need to communicate with via a serial port.

It's a two way communication, I send some data to the device, it sends some back.

I understand linux treats serial ports as terminals, the one I want to deal with is /dev/ttyS0.

I've used a little gui program called GtkTerm to try to communicate with it, and it sends data but doesn't seem to be able to receive any.  

So, as I understand it I can open a terminal to /dev/ttyS0 and then simply enter my data, and receive incoming data, a bit like the old HypterTerminal in windows.  Only thing is, I have no idea how to do that!

---

### Post by tCarls on 2007-05-03
To send data you can just echo your data and redirect it to the serial port. Like this
```

echo "send this" > /dev/ttyS0

```

I don't remember how to receive data from the serial port, but I know it's possible because I used to do it. Lately I've been using perl. The serial port perl module is here: [http://search.cpan.org/~cook/Device-SerialPort-1.002/SerialPort.pm](http://search.cpan.org/~cook/Device-SerialPort-1.002/SerialPort.pm)

Here's a skeleton script that sends a string to /dev/ttyS0 then reads data from /dev/ttyS0 and stores it in a variable.

```

#!/usr/bin/perl -w
use strict;

use Device::SerialPort; 

my $port = Device::SerialPort->new("/dev/ttyS0");

$port->baudrate(115200);
$port->parity("none");
$port->handshake("none");
$port->databits(8);
$port->stopbits(1);
$port->read_char_time(0);
$port->read_const_time(1);

# send data out
$port->write("send this text to serial port");
sleep(1);

# read data until new data is not found five times in a row
my $readData = &read(5);
 
$port->close();

sub read()
{
	my $maxCnt = shift;
	my $notFndCnt = 0;

	# clear the read buffer variables
	my $readChars = 0; my $readBytes = ""; my $readBuffer = "";


	while ($notFndCnt < $maxCnt) {
		# Read serial port data
		($readChars, $readBytes) = $port->read(1);

		print $readBytes;

		$readBuffer .= $readBytes;

		if ($readChars == 0) {
			$notFndCnt++;
		} else {
			$notFndCnt = 0;
		}
	}

	print "\n";

	$readBuffer;
}

```

Of course that doesn't do you much good if you don't know perl. But I hope it helps. Maybe someone else knows how to read from a shell.

---

### Post by musther on 2007-05-04
I don't know perl I'm afraid, but let me explain what I'm attempting to do.

I am visually impaired and use an external speech synth which is a serial device.  Outputting text to it:

echo "Hello world." >> /dev/ttyS0

Produces text, nice and easy.

What I want to do is convince somebody (I'm not a programmer, but I do do some scripting) to write me a little program which will take in a large text file (say a book) and then send it to the serial port one sentence at a time.  It needs to have a few other features, but basically that's it.  The problem is you have to know when it's finished speaking so you can send the next sentence, this is achieved by sending a special command (I think it's something like @l?) and grabbing the response.  Thing is, before I can convince somebody to write this for me, I need to be able to tell them what the commands and response are.

---

### Post by tCarls on 2007-05-04
That doesn't sound like it would be very hard to do. In fact, you could probably do it by adding only a few lines to the code I posted. Since nobody else posted about how to do this from a shell, would you be willing to try it in perl?

perl should be already installed. You can get the serial module here: [http://search.cpan.org/CPAN/authors/id/C/CO/COOK/Device-SerialPort-1.002.tar.gz](http://search.cpan.org/CPAN/authors/id/C/CO/COOK/Device-SerialPort-1.002.tar.gz)
Install it like this:
```

tar -xzvf Device-SerialPort-1.002.tar.gz
cd Device-SerialPort-1.002
./configure
perl Makefile.PL
make
sudo make install

```

You can see the results of commands by running the code I posted earlier. Save it in a file called "serial.pl" or whatever and make it executable then run "./serial.pl". But first modify the $port->write line to write "@!?". You might also need to modify the baudrate, parity, etc. That information should be in your device manual. After doing that post the output here. I can write the rest for you. It shouldn't be more than 100 lines of code.

The only problem would be if "@!?" isn't the correct command to send. Figuring out the response of the command is easy, but figuring out the correct command to send doesn't seem possible without a manual.

---

### Post by musther on 2007-05-04
This thread talks about what I want to do:

[http://ubuntuforums.org/showthread.php?p=2594449#post2594449](http://ubuntuforums.org/showthread.php?p=2594449#post2594449)

let me know when you've had a look and if you still think you can help me.

Thanks

---

### Post by mjbeam on 2007-05-12
Musther,

Which device do you have connected to your serial port? If we know the device maybe we can find the technical documentation online.


-Mike

---

### Post by musther on 2007-05-12
I've got the technical documentation, the device is called a 'Juno' and the documentation is attached.

---

### Post by mjbeam on 2007-05-12
> **musther said:**
> I have a device I need to communicate with via a serial port.

It's a two way communication, I send some data to the device, it sends some back.

I understand linux treats serial ports as terminals, the one I want to deal with is /dev/ttyS0.

I've used a little gui program called GtkTerm to try to communicate with it, and it sends data but doesn't seem to be able to receive any.  

So, as I understand it I can open a terminal to /dev/ttyS0 and then simply enter my data, and receive incoming data, a bit like the old HypterTerminal in windows.  Only thing is, I have no idea how to do that!

Hello again Musther.

What happens if you send a fairly long line of text to your synthesizer with GTKTerm, then while it's still talking send "@I?" (not with the quotes of course)

Do you get a response from the synthesizer then? According to the documentation you should receive back something like:

I02T

You may first (before you even send the line of text to the synthesizer) have to increment the index on the synthesizer by sending "@I+" (without the quotes). Then send the line of text. Then while it's talking send "@I?"

Try that and let me know what happens.


Thanks...Mike

---

### Post by musther on 2007-05-12
I've already tried that, and I get back:

I00T

And when it has finished:
 
I00M

I only get 00 because indexing is turned off.

Before I can get any response I have to issue:

@YF3N8

to get it into full duplex mode.

---

### Post by mjbeam on 2007-05-13
Nice! That's what I was hoping for. I'll try to put together a quick C application that will output a small text file to the serial port, one line at a time (waiting for I00M to come back from the synthesizer before sending the next line) and have you test it out. 

Do you know how to compile a C file? It's OK if you don't. I'll show you how.


-Mike

---

### Post by musther on 2007-05-13
I've done compilation of programs with make, but beyond that I'll have to learn.

Thanks very much for your help!

---

### Post by mjbeam on 2007-05-13
I have something put together but I'm at work right now and I want to test it first (as much as I can with out a synthesizer) before I send it to you. I'll have to do that when I get home.  Perhaps we should move this discussion to email? My address is in my profile under Biography.


-Mike

---

### Post by thelinuxguy on 2007-05-13
Hello,
I cannot offer any help at the moment but have been following this thread and I would appreciate if you keep the discussion here itself and not via email. I am sure many others would want to know the solution as well.

Thanks.

---

### Post by musther on 2007-05-13
I'm more than happy to keep this thread up to date with the progress we make towards a solution, but don't think it's worth filling it up with every little commend and issue with the code etc.

Watch this space!

---

### Post by thelinuxguy on 2007-05-14
Thanks. I am waiting eagerly.

---

