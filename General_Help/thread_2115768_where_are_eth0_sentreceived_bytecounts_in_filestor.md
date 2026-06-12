---
title: "where are eth0 sent/received bytecounts in filestore"
date: 2013-02-13
forum: General Help
---

### Post by palloy on 2013-02-13
Lubuntu 12.10 > System Tools > System Profiler > Network > Interfaces > 
shows the bytes sent and received for all interfaces including eth0.
Where are these figures kept in the file system?
It looks like the figures in System Profiler are updated every 3 seconds , but are they available at, say, 1 second intervals somewhere ?  Can this interval be changed by some setting?

I would like to capture these numbers in an app, calculate bytes/second, and make them available across the LAN. Does any existing app do this?

---

### Post by lmarmisa on 2013-02-13
You could call a command similar to this from your application (this is an example):

```

ifconfig eth0 | grep 'RX bytes'

```The output will be something like this:

```

          RX bytes:162481 (162.4 KB)  TX bytes:66697 (66.6 KB)

```Scan your desided data and manage them according your needs.

I hope this method could help you.

---

### Post by lmarmisa on 2013-02-13
I have found the folders where the interface stats are stored. 

Take a look to the folder /sys/class/net/eth0/statistics.

```

-r--r--r-- 1 root root 4096 Feb 14 04:29 collisions
-r--r--r-- 1 root root 4096 Feb 14 04:29 multicast
-r--r--r-- 1 root root 4096 Feb 14 04:29 rx_bytes
-r--r--r-- 1 root root 4096 Feb 14 04:29 rx_compressed
-r--r--r-- 1 root root 4096 Feb 14 04:29 rx_crc_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 rx_dropped
-r--r--r-- 1 root root 4096 Feb 14 04:29 rx_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 rx_fifo_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 rx_frame_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 rx_length_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 rx_missed_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 rx_over_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 rx_packets
-r--r--r-- 1 root root 4096 Feb 14 04:29 tx_aborted_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 tx_bytes
-r--r--r-- 1 root root 4096 Feb 14 04:29 tx_carrier_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 tx_compressed
-r--r--r-- 1 root root 4096 Feb 14 04:29 tx_dropped
-r--r--r-- 1 root root 4096 Feb 14 04:29 tx_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 tx_fifo_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 tx_heartbeat_errors
-r--r--r-- 1 root root 4096 Feb 14 04:29 tx_packets
-r--r--r-- 1 root root 4096 Feb 14 04:29 tx_window_errors

```File contents are text.

More ideas here: [http://frankpzh.wordpress.com/2011/04/12/use-python-to-collect-performance-data/](http://frankpzh.wordpress.com/2011/04/12/use-python-to-collect-performance-data/)

---

### Post by DuckHook on 2013-02-14
> **palloy said:**
> I would like to capture these numbers in an app, calculate bytes/second, and make them available across the LAN. Does any existing app do this?

You are basically asking to do network administration. There are so many tools that it would make your head spin, but the one you are looking for is ntop, which will give you more info than you can shake a stick at.

```
sudo apt-get install ntop
```ntop is read in your web browser and gives you charts, numbers and minutiae to satisfy even the finest picker of nits. It is also highly configurable, but there are so many options that you will need to google for usage and read the ntop man page.

---

### Post by palloy on 2013-02-14
Thanks for all that help, much appreciated - it has given me a lot to think about.
I guess I'll try ntop first, but the frankpzh link was more the kind of level I was thinking of.

---

### Post by DuckHook on 2013-02-14
After installing, be sure to read the man page. It is massive but don't let it intimidate you. You really only need to figure out how to see it on your web browser. Once installed, ntop loads a daemon process that collects data quietly in the background. You read this data on a simple web page that a child could navigate. ntop will also let you collect info from other machines on your network, although that is a little more advanced. To start out, just point your browser to the ntop database of your own box by using the following URL:

[http://localhost:3000](http://localhost:3000)

3000 is the default port number ntop uses to report its data. After entering the first time, just bookmark it for future visits. If you've closed this port off on your firewall, you may need to open it for your localhost. It does not have to be open to the outside world (unless you want to read your data from a remote machine). Their on-line documentation is [here]("http://www.ntop.org/support/documentation/").

---

### Post by palloy on 2013-02-16
ntop installed with a bit of difficulty and is now running OK.
That is a lot of information!
It seems to be doing the same kind of thing as BitmeterOS, only more so. I guess I really will have to read the manual to see if I can reduce the amount of detail, which BitmeterOS can't do.

I'm hoping to install it on all my machines, and pull all the information together on one screen. I have written a web page with 4 iframes so I  can (theoretically) see them all at the same time, but that doesn't give me actual access to the data for totalling across the LAN.

Just thinking aloud:
If I make /sys/class/net/eth0/statistics/ a Samba share on each box and read rx_bytes and tx_bytes from each box every second, would that have less overheads or more?

Or is it possible to pipe the output of ifconfig to a file on the controlling box?

---

### Post by palloy on 2013-02-21
This is the solution I have come up with, using PHP (CLI).

```
<?php // bandwidth server for Ubuntu 
$socket = stream_socket_server('tcp://0.0.0.0:3080', $errno, $errstr ); 
if (!$socket) { echo ($errno . " - " . $errstr . "\r\n"); exit(0); } 
echo ("Listening on port 3080\r\n" ); 
while (true)  
{    $client = stream_socket_accept($socket, 86400); 
    if(!$client) {echo (date('H-i-s ') . "Connection failed\r\n"); continue;} 
    // 
    $rx = fopen('/sys/class/net/eth0/statistics/rx_bytes', 'r'); 
    $rxbytes = trim(fgets($rx, 80)); 
    fclose($rx); 
    // 
    $tx = fopen('/sys/class/net/eth0/statistics/tx_bytes', 'r'); 
    $txbytes = trim(fgets($tx, 80)); 
    fclose($tx); 
    // 
    $report = date('H-i-s ') . $rxbytes . " " . $txbytes  ; 
    $result = fwrite($client, $report, strlen($report)); 
    echo ($report . "\r\n"); 
    fclose($client); 
} 
?>
```

This example client only goes as far as capturing data from one server, and no calculations:
```

<?php // bandwidth client 
while (true) 
{    $server = stream_socket_client('tcp://192.168.0.4:3080', $errorno, $errorstring, 1); 
    if (!$server) { echo ("stream_socket_client error: " . $errorno . " - " . $errorstring . $crlf ); exit(0); } 
    $response = fgets($server, 80); 
    echo ($response . "\r\n"); 
    usleep(920000);    // needs fine tuning
} 
?>
```It needs a slightly different approach for Win 7 server:
```
<?php // bandwidth server for Win 7 
$socket = stream_socket_server('tcp://0.0.0.0:3080', $errno, $errstr ); 
if (!$socket) { echo ($errno . " - " . $errstr . "\r\n"); exit(0); } 
echo ("Listening on port 3080\r\n" ); 
$lines = array(); 
while (true)  
{    $client = stream_socket_accept($socket, 86400); 
    if(!$client) {echo (date('H-i-s ') . "Connection failed\r\n"); continue;} 
    unset($lines); 
    exec('netstat -e', $lines ); 
    $report = date('H-i-s ') . substr($lines[4], 24) ; 
    $result = fwrite($client, $report, strlen($report)); 
    echo ($report . "\r\n"); 
    fclose($client); 
} 
?>
```

I hope that helps someone.

---

