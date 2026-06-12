---
title: "[SOLVED] Input/output redirect/pipe problems"
date: 2007-05-19
forum: General Help
---

### Post by olejorgen on 2007-05-19
Hi, I'm trying to automate a kinda cumbersome telnet process (adding port forwarding). 

I thought I could do it by simply "piping" the content of a file containing the commands to telnet.
ie.
```
cat telnet_addport | telnet
```
but it does not work. The output is:
```

telnet> Trying 10.0.0.1...
Connected to 10.0.0.1.
Escape character is '^]'.
Connection closed by foreign host.
```
whereas the normal output is:
```

telnet> o 10.0.0.1 
Trying 10.0.0.1...
Connected to 10.0.0.1.
Escape character is '^]'.
Username : Administrator
Password : 

```
I really don't get why this won't work, isn't telnet simply waiting for input on stdin, and the pipe is delivering input to stdin? Why is the piping approch different from actually typing the commands?


telnet_addport: (yeah, empty password)
```

o 10.0.0.1
Administrator

nat
maplist
mapadd
TypeB_1

xx.xxx.xxx.xxx
10.0.0.2



9998
9998

exit

```

---

### Post by mbradlcu on 2007-05-20
I believe the telnet command gets the entire contents of the file and it's not parsed per telnet response. If ssh is an option I could be greater help with a solution.

---

### Post by olejorgen on 2007-05-20
Nope :( It's a speedtouch ruter, only telnet available.

But I still don't get the difference... When telnet is waiting for a username, isn't it simply doing something like this (in effect): string = stdin.readline() ? 

Hm. when I think about it, I guess telnet is simply sending the characters directly to the server as fast as it can. (That's why backspace wont work without settting line mode?) :-/

Maybe if I obtained pipes for stdin and stdout and waited for output from stdout before sending more commands to stdin? (using eg. python?) Any idea how I'd to that?

---

### Post by olejorgen on 2007-05-20
Ok, I managed to do it with python. Very crude solution follows:
```

#!/usr/bin/python

import os
import sys
import time
import thread

i,o=os.popen2("telnet")

def stdout_flush():
	while(1):
		str = o.readline()
		if str == "":
			break
		print str,

thread.start_new_thread(stdout_flush,())

def w(cmd):
	i.write(cmd+"\r")
	i.flush()

cmd = sys.stdin

w("o 10.0.0.1\n")
time.sleep(.5)
w("Administrator")
time.sleep(.5)
w("")
time.sleep(.5)
for line in cmd:
	line = line.replace("{ip}", sys.argv[1].strip())
	line = line.replace("{outp}", sys.argv[2].strip())
	line = line.replace("{inp}", sys.argv[3].strip())
	w(line)
	time.sleep(.3)

```

---

### Post by olejorgen on 2007-05-20
Behold:
```

#!/usr/bin/python

import os
import sys
import time
import thread
from optparse import OptionParser

# Todo:
# - Add options for username, password, telnet_addr and telnet_cmd
# - Add "set default" commands
# - Fix waiting mess and verbose command

### @config:
outside_addr_default = "xx.xxx.xxx.xxx"
large_delay = 0.1
small_delay = 0.05
telnet_cmd = "telnet"
username = "Administrator"
password = ""
telnet_addr = "10.0.0.1"
verbose = True
### @end

### @commands:
maplist_cmd = "nat maplist"
mapadd_cmd = "nat mapadd intf=TypeB_1 outside_addr=%s inside_addr=%s outside_port=%s inside_port=%s"
mapdelete_cmd = "nat mapdelete intf=TypeB_1 index=%s"
### @end

tel_in = None
tel_out = None

def stdout_flush():
	while(1):
		str = tel_out.readline()
		if str == "":
			break
		if verbose:
			print str,

def do(cmd):
	tel_in.write(cmd+"\r")
	tel_in.flush()

def wait(n):
	time.sleep(n)

def login(addr, username, password):
	do("o " + addr + "\n")
	wait(large_delay)
	do(username)
	wait(large_delay)
	do(password)
	wait(large_delay)

def maplist():
	do(maplist_cmd)
	wait(1)

def mapadd(inside_addr, inside_port, outside_port = None, outside_addr = None):
	if outside_addr == None:
		outside_addr = std_outside_addr
	if outside_port == None:
		outside_port = inside_port
	cmd = mapadd_cmd % (outside_addr, inside_addr, outside_port, inside_port)
	do(cmd)
	wait(small_delay)
	
def mapdelete(index):
	cmd = mapdelete_cmd % index
	do(cmd)
	wait(small_delay)

def start_telnet():
	global tel_in, tel_out
	tel_in, tel_out = os.popen2(telnet_cmd)

def close_telnet():
	do("exit")
	wait(small_delay)
	tel_in.close()

def main():
	global verbose
	global outside_addr
	usage =  "usage: %prog [-v, -l][-a | -d] args"
	parser = OptionParser(usage)
	parser.add_option("-v", "--verbose", action="store_true", dest="verbose", default=verbose,
				help = "verbose output")
	parser.add_option("-l", "--list", action="store_true", dest="list", default=False,
				help = "list the nat mappings (happens after possible command)")
	parser.add_option("-a", "--add", action="store_true", dest="add", default=False,
				help = "add a nat mapping. (args: inside_addr, port [outside_port, [outside_addr]])")
	parser.add_option("-d", "--delete", action="store_true", dest="delete", default=False,
				help = "delete a nat mapping. (args: index)")
	
	options, args = parser.parse_args()
	
	verbose = options.verbose
	
	start_telnet()
	login(telnet_addr, username, password)
	thread.start_new_thread(stdout_flush,())
	
	if options.delete:
		mapdelete(args[0])
	elif len(args) > 1:
		inside_addr = args[0]
		inside_port = args[1]
		outside_port = inside_port
		if len(args) > 2:
			outside_port = args[2]
		if len(args) > 3:
			outside_addr = args[3]
		mappadd(inside_addr, inside_port, outside_port, outside_addr)
	if options.list:
		maplist()
	wait(large_delay)
	close_telnet()


if __name__ == "__main__":
	main()

```

I've probably used 1000 times the time I'll ever save on this project ^^

---

### Post by altonbr on 2007-12-19
I wish I knew what this thread was about...

---

### Post by olejorgen on 2007-12-21
How to make a telnet script?

---

