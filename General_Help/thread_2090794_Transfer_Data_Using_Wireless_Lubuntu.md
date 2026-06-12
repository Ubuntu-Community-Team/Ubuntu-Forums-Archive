---
title: "Transfer Data Using Wireless Lubuntu"
date: 2012-12-03
forum: General Help
---

### Post by dnhan on 2012-12-03
Hi all, I'm doing work for a 4th year project for university involving sending wireless data in order to control a small robot.

I have Lubuntu 10.04 set up and running on a small computer board which is attached to a small robot. However, the board is quite weak in terms of hardware so I would like to send the data using a wireless USB device to a server which would then process the data and transmit data back to the board. 

I'm kind of confused in terms of how to start on this, so can anyone help me get started?

---

### Post by SteveDee on 2012-12-12
You haven't provided a lot of info, so not sure exactly what you need help with. But as you haven't had a response, here is a simple scheme to get the ball rolling.

 - Create a network shared folder on your robot computer.
 - Write data from your robot into a file (text, csv, html or whatever) into the shared folder.
 - Create a program on your server to read this file at regular intervals & write instructions back to a second shared file in the robot shared folder.
 - Read and execute robot commands from the second file.

---

