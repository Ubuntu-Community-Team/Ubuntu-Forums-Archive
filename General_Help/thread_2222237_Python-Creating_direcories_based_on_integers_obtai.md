---
title: "Python-Creating direcories based on integers obtained froma string."
date: 2014-05-05
forum: General Help
---

### Post by ethereal-rod on 2014-05-05
Currently, my code searches fro all XML files within a directory and renames the files based on certain fields, the next step is use one of those
fields "fecha" as a means to organize those files. so of course one directory should be named "2014" and inside of it should be 12 directories
"01,02,03,04...12"

fecha is actually a string  separating year, month and day with a hyphen, I mean to split it in the following way.

----///

a,b=[ int(fecha) for fecha in fecha.split("-") ]

----///

Having done this, now I can create directories based on the year "a" and month "b" and then store the xml file, if the directory already exists
then it should just sae it there.
Any further insight as to how to complete the next step would be greatly apreciated.



#encoding:utf-8
import os, glob
import xml.etree.ElementTree as ET
from sys import argv


try:
    script, directory = argv
    directory_renames = directory
    directory += '/*.xml'
except:
    directory = '*.xml'

files = glob.glob(directory)

for file in files:
    tree = ET.parse(file)
    root = tree.getroot()

    fecha = root.attrib['fecha'].strip()[2:10] # fecha de Comprobante
    total = root.attrib['total'] # total de Comprobante
    nombre = root[0].attrib['nombre'] # nombre de Emisor
    nombre = nombre.replace(' ','').replace(',','').replace('.','').upper()
    try:
        municipio = root[0][1].attrib['municipio'] # municipio de Emisor con ExpedidoEn
    except:
        municipio = root[0][0].attrib['municipio']
    municipio = municipio.replace(' ','').replace(',','').replace('.','').upper()

    fileName = fecha+'_'+municipio+'_'+nombre+'_$'+total+'.xml'

    if len(directory) > 5:
        os.rename(file, directory_renames+'/'+fileName)
    else:
        os.rename(file, fileName)

---

