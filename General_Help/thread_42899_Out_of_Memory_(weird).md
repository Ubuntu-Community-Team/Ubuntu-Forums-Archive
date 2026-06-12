---
title: "Out of Memory (weird)"
date: 2005-06-19
forum: General Help
---

### Post by lozzd on 2005-06-19
Why does all the weird stuff happen to me?

I went out this morning with my Apache server (apache2) on my ubuntu box (2x2ghz xeons, 2gb of ram) quite happily.

Came back this evening to find my bash terminal full of "Out of memory: killing process xxxx"

It had killed pretty much everything. Weird, I thought, nm, just a memory leak or something.. I'll just reboot.

Rebooted, X started, In GDM and all of a sudden the mouse locks up.  Checked PHPSysInfo which loaded (eventually) and showed a load average of 50 (!) something... but the memory usage was still only about 300 mb out of 2gb, pretty normal for 60 or so apache childs. It normally runs up to 200 at peak times with no problems at all!

So I reboot again, and quickly stop GDM and sit in the terminal, thinking something is wrong with X, and watching the Apache status page, all was fine for a while until again, it slowed to a crawl with loading pages, and sure enough, it was killing apache processes again.

How come this worked before, I changed nothing and all of a sudden my 2gb of ram is being used like its 400mb or something?! 

I am completly baffled by this, and not the most experienced of linux users, so if anyone could shed any light that'd be fantastic!

Sorry for the essay! (if you didnt read it, please do btw!)

Thanks in advance,
Laurie "if theres a strange problem no-ones ever heard of i'll get it" Denness  ](*,)

---

### Post by intangible on 2005-06-20
Are you using common PHP scripts, or something custom?  It is possible one of your php scripts has a runaway loop.

Keep us updated.

---

### Post by lozzd on 2005-06-20
[QUOTE=intangible]Are you using common PHP scripts, or something custom?  It is possible one of your php scripts has a runaway loop.

Keep us updated.[/QUOTE]

Thanks, I didn't think of that. I use two custom PHP scripts to produce "Recently Played" (music) signatures, and most of my hundreds of thousands of requests a day (80%)  are for them. And at the peak time theres over 8 requests a second for them.
One thing I have just noticed is theres over 10,000 temporary image files that it creates, maybe it didn't like going over 10,000 because it was only just over it.

In the apache error log, I've got "Segmentation fault" on the process when it exits. 

Thanks for your help.
Anyone else any ideas? I will post the script if it helps.

Laurie

---

### Post by lozzd on 2005-06-20
This is driving me crazy. 
Why would it work and all of a sudden stop 12 hours later and refuse to work again?

I've narrowed down the script to a PHP script that is the most used on the server. I'm not sure whether it actaully is this script, or i just suspect it because its the most used, but I left the server running with the files not in www and i didn't get any processes killed.
It even starts killing things like gdmgreeter. Even though I have (supposedly, reported by top and system moniter) over a gigabyte of RAM left. 

I'll post the code here, but I'm not entirely sure how that can help when the code worked before, hasn't been modified and all of a sudden doesn't now. Its quite fustrating. 

index.php: 
```

<?php

/* copyright and all that stuff (c) steve[at]thecommunion.co.uk (audioscrobbler user:mokele) */
//
// This script uses certain methods to cache the image that is generated.  The $cache_time, variable
// specifies how long the image should be cached for before the audioscrobbler feed is read again.
// This method produces less strain on the audioscrobbler servers than it would if it had to regenerate
// the image every time it is viewed.  This is a required feature, and should not be disabled or hacked.

//do not edit this define lines
define('ALT_ROW', 0);
define('ALT_COLUMN', 1);
define('ALT_CELL', 2);
define('READ_XML_FEED', 0);
define('READ_TXT_FEED', 1);
define('DEBUG', false);  //development only, true = access local rssfeed and no image caching
define('BENCH', false); //turns on bench timing, and doesn't output the image
///////////////////////////////////
// DO NOT EDIT _ABOVE_ THIS LINE //
///////////////////////////////////

// DO edit these options directly below
// All the options below may seem a bit messy, but it's just the way it works, play around with them! :D

$use_args = true;//* set this to true if you want to allow all allowable options to be editable via the query string arguments
				  //see the wiki page for documentation on what arguments are supported.  This will allow ANYONE
				  //to use this script via your hosting, unless you supply a whitelist(see below).
				  //* Set this to false to hardcode the options for one user.
				  //* See the wiki for another way to set this variable.  It allows you to specifiy a limited number of options
				  //available to users of this script.  E.g. You may want everyone to be able to use this script via changing
				  //the username, but not change the appearance.  You may want to keep the script to yourself and change other options
				  //for you on different sites.
				  
$whitelist = false;	//set this to the filename of a whitelist which contains a word boundry(space, tab, return, etc)
					//delimited list of usernames of users who are allowed to use this script if $use_args allows changing of $user

$feed_type      = READ_XML_FEED;
$feed_timeout   = 10; //number of seconds to wait for the feed from the audioscrobbler servers
$user           = 'lozzd';     //your username
$timezone       = 'UTC';        // The shorthand characters for your timezone (UTC, CST, GMT, or empty '', etc)
$timezone_alt   = 0;           // enter the alteration your timezone is, as the current feed doesn't seem to display it correctly.
$cache_time     = 300;          // Seconds to keep the cache for (e.g. 240=4 minutes). Do not set too low, or it will cause unecessary
								// strain on the audioscrobbler servers.
$cache_filename = $user.'.png'; //filename to cache as.  Default = yourusername.png
								//This is ignored and set to $user_$show.png if $use_args is true

//if $use_args === true, then these are the default options which could be overridden
$options = array(
	'font'           => '/var/www/Vera.ttf', //REQUIRED - default font, and font for the url
	'padding'        => 2,          //REQUIRED - cell padding
	'fontsize'       => 7,          //REQUIRED - default text size, and text size for the url
	'spacing'        => 1,			//REQUIRED - defines the spacing between cells, can be 0 if you wish.
	'border'         => 1,			//REQUIRED - but can be set to 0 if you so wish.
	'antialias'      => true,	    //REQUIRED - antialias the fonts
	'show'           => 4,		    //REQUIRED - the number of items to show
	'headertext'      => 'Recently Played Tracks:',	//REQUIRED - puts a row at the top with this text.
													//Setting to false or '' turns it off.  (no quotes required for false value)
	'headeralign'     => 'left',	//if headercolumn !== false chooses what alignment it is to be.
	'erroralign'     => 'center',   //REQUIRED - alignment of error messages if the feed is empty or can't be accessed.
	'urlalign'       => 'right',    //REQUIRED - alignment of your URL at the bottom.  Set to false (no quotes required for false value) if it is not required
								//e.g. 'url align' => false or 0 or empty string ''
	'width'      => 350,	    //REQUIRED - the width of the image
	'bgstyle'    => ALT_ROW,    //REQUIRED - is either ALT_ROW, ALT_COLUMN, or ALT_CELL
	'colors' => array( // all colors are here because they are batch converted to rgb before rendering
		'bg'     => 'FFFFFF',   //REQUIRED - Background color, visible through cell spacing
		'bg1'    => 'F0F0F0',   //REQUIRED - alternate background color 1
		'bg2'    => 'F9F9F9',   //REQUIRED - alternate background color 2
		'border' => 'DDDDDD',   //REQUIRED/OPTIONAL - if the image 'border' is set to 0(zero) then this is never used.
		'text'   => '444444',   //REQUIRED - row text, and other fields if they haven't been set.
		'num'    => 'AAAAAA',   //OPTIONAL - DEFAULTS TO text
		'artist' => '1F67B7',   //OPTIONAL - DEFAULTS TO text - song artist
		'title'  => '444444',   //OPTIONAL - DEFAULTS TO text - song title
		'date'   => '444444'    //OPTIONAL - DEFAULTS TO text - listen to date
	),
	'fields' => array( //each field can have 'align', 'fontsize', and 'font'
					   // align is REQUIRED
					   // artist and title fields cannot be used in READ_TXT_FEED mode
					   // the description is rendered as '<artist> - <title>' when in READ_XML_FEED mode
		'num' => array(
			'align'    => 'center',
			//'fontsize' => 9
		),
		'description' => array(
			'align' => 'left'
		),
		// Try uncommenting the two fields 'artist', and 'title',
		// and commenting out 'description' above and see what happens ;)
		/*********
		'artist' => array(
			'align' => 'left',
		), 
		'title' => array(
			'align'    => 'left',
			'fontsize' => 8
		),
		*********/
		'date' => array(
			'align' => 'center'
		)
	)
);

/////////////////////////////////
// DO NOT EDIT BELOW THIS LINE //
/////////////////////////////////

include 'RPI.php';
if( $use_args !== false ) fetchArguments(&$options, $use_args);
new RPI($user, $feed_type, $cache_filename, $cache_time, $whitelist, $options);



?>

```

RPI.php:
```

<?php
class RPI
{
	function RPI($user, $feed_type, $cache_filename, $cache_time, $whitelist, $options)
	{
		//BENCH + DEBUG CODE
		if(DEBUG===true && BENCH!==true) $cache_time = 0;
		if(BENCH===true) {
			require 'Benchmark/Timer.php';
			$GLOBALS['timer'] = new Benchmark_Timer();
			$GLOBALS['timer']->start();
		} 
		//END BENCH CODE
		
		
	
		if( $GLOBALS['whitelist'] !== false )
		{
			$whitelist_file = file_get_contents($whitelist);
			if( !preg_match("/(\b)$user(\b)/", $whitelist_file) )
			{
		  		die('This version of RecentlyPlayedImage is only usable by specific "whitelisted" audioscrobbler users.  If you should be whitelisted and currently aren\'t then please contact the host of this script.');
			}
		}
		
		$table =& new ImageTable($user, $options);
		
		if(BENCH===true)
			$GLOBALS['timer']->setMarker('Checking Cached');

		$gen_image = !file_exists($cache_filename) || (filemtime($cache_filename) < time()-$cache_time);
	
		if($gen_image)
			$data = $feed_type==READ_XML_FEED ? $this->readXMLData($user) : $this->readTXTData($user);

		if( isset($data) && !is_array($data) && file_exists($cache_filename) )
		{
			touch($cache_filename); //act as though it's just been generated
			$gen_image = false;
		}

		if( $gen_image )
		{
			$table->setData(&$data);
			$table->render();
			$im =& $table->getImage();
			
			//BENCH CODE
			if(BENCH===true)
				$GLOBALS['timer']->setMarker('Saving Cached Image');
			
			$res = imagepng($im, $cache_filename);
			if( !$res )
				die("You have not given this directory the correct permission for this script to cache the generated image.  Please give this directory full write permission by all (linux/unix chmod 777).  This causes less strain on the Audioscrobbler servers.  This is a required feature, and should NEVER be removed (as we have been told by the Audioscrobbler dev team).  Thank you!");
		} else {
			//BENCH CODE
			if(BENCH===true)
				$GLOBALS['timer']->setMarker('Reading Cached Image');
			$im = imagecreatefrompng($cache_filename);
		}
		
		//BENCH CODE
		if(BENCH===true) {
			$GLOBALS['timer']->stop();
			$GLOBALS['timer']->display();
			exit;
		}
		//END BENCH CODE
		
		header("Content-type: image/png");
		imagepng($im);
		imagedestroy($im);
		exit;
	}
	
	function readXMLData($user)
	{
		//BENCH CODE
		if(BENCH===true)
			$GLOBALS['timer']->setMarker('Reading XML Feed');
		
		$xml = @file_get_contents(DEBUG===true ? 'aliguana.xml'
			             : 'http://ws.audioscrobbler.com/rdf/history/'.$user);
		if($xml===false) return false;
		
		//BENCH CODE
		if(BENCH===true)
			$GLOBALS['timer']->setMarker('Parsing XML Feed');
		//if( preg_match('/<title>Audioscrobbler :: Planned Downtime<\/title>/', $xml) )
			//return false;

		$xml_parser = @xml_parser_create();
		@xml_set_element_handler($xml_parser, "startElement", "endElement");
		@xml_set_character_data_handler($xml_parser, "cdataHandler");
		
    	if (!@xml_parse($xml_parser, $xml, true)) {
		   return false;
    	}
		@xml_parser_free($xml_parser);
		
		return isset($GLOBALS['rpi_tracks']) ? $GLOBALS['rpi_tracks'] : array();
	}
	
	function readTXTData($user)
	{
		//BENCH CODE
		if(BENCH===true)
			$GLOBALS['timer']->setMarker('Reading TXT Feed');
		
		$txt = @file_get_contents('http://ws.audioscrobbler.com/txt/recent/'.$user);
		if($txt===false) return false;
		
		//BENCH CODE
		if(BENCH===true)
			$GLOBALS['timer']->setMarker('Parsing TXT Feed');
		$data = array();
		$lines = explode("\n", $txt);

		for($i=1, $j=1; $i<count($lines); $i+=2)
		{
			if( empty($lines[$i]) ) continue;
			//echo "$i, $j, {$lines[$i]}<br>";
			$data[$j] = array( 'num' => $j++, 'description' => $lines[$i], 'date' => $lines[$i+1] );
		}
		return $data;
	}
}

class ImageTable
{
	var $im = false;
	var $user;
	var $width = 0, $height = 0;
	var $data = array();
	var $options;
	function ImageTable($user, $options)
	{
		$this->user = $user;
		$this->width = $options['width'];
		$this->options = $options;
	}
	function setData(&$data)
	{ $this->data = $data; }
	function setOptions(&$options)
	{ $this->options = $options; }
	function &getImage()
	{ return $this->im; }
	
	function _convertColors()
	{			
		foreach($this->options['colors'] as $name => $color)
		{
			$this->options['colors'][$name] = imagecolorallocate($this->im,
				hexdec(substr($color,0,2)),
				hexdec(substr($color,2,2)),
				hexdec(substr($color,4,2))
			);
		}
	}
	
	function _calculateSizes()
	{			
		$maxheight = 0;
		$maxwidth = 0;
		foreach($this->options['fields'] as $field => $options)
		{
			$i = 0;
			foreach($this->data as $id => $track)
			{
				list($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly) =
					imageftbbox(
						isset($this->options['fields'][$field]['fontsize']) ? $this->options['fields'][$field]['fontsize'] : $this->options['fontsize'],
						0,
						isset($this->options['fields'][$field]['font']) ? $this->options['fields'][$field]['font'] : $this->options['font'],
						$track[$field],
						array()
					);
				list($width, $height) = $this->widthAndHeight($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly);
				
				
				$maxwidth = max($width, $maxwidth);
				$maxheight = max($height, $maxheight);
				if(++$i>=$this->options['show']) break;
			}
			$i = 0;
			foreach($this->data as $id => $track)
			{
				$this->data[$id]['width'][$field] = $maxwidth;
				if(++$i>=$this->options['show']) break;
			}
			$maxwidth = 0;
			
		}
		$i = 0;
		foreach($this->data as $id => $track)
		{
			foreach($this->options['fields'] as $field => $options)
			{
				$this->data[$id]['height'][$field] = $maxheight;
			}
			$this->height += $maxheight + $this->options['spacing'] + 2*$this->options['padding'];
			if(++$i>=$this->options['show']) break;
		}

	}
	
	var $y = 0;
	var $x = 0;
	var $altbg = false;
	function render()
	{
		//BENCH CODE
		if(BENCH===true)
			$GLOBALS['timer']->setMarker('Rendering');
			
		////// EMPTY RPI
		if( empty($this->data) || !is_array($this->data) )
		{
			$msg = $this->data === false
			    ? 'Error Recieveing \'recently played\' tracks.'
				: 'No \'recently played\' tracks to display at present.';
				
			$this->data = array();
			list($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly) = imageftbbox(
					$this->options['fontsize'],
					0,
					$this->options['font'],
					$msg,
					array()
				);
			list($msgwidth, $msgheight) = $this->widthAndHeight($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly);
			$this->height += $msgheight + $this->options['spacing'] + 2*$this->options['padding'];
		}
		////// EMPTY RPI	
		
		////// URL ROW
		if( $this->options['urlalign'] !== false && !empty($this->options['urlalign']) )
		{
			$url = 'http://www.audioscrobbler.com/user/'.$this->user;
			list($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly) = imageftbbox(
					$this->options['fontsize'],
					0,
					$this->options['font'],
					$url,
					array()
				);
			list($urlwidth, $urlheight) = $this->widthAndHeight($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly);
			$this->height += $urlheight + $this->options['spacing'] + 2*$this->options['padding'];
		}
		/////// URL ROW
		
		////// HEADER ROW
		if( $this->options['headertext'] !== false && !empty($this->options['headertext']) )
		{
			list($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly) = imageftbbox(
					$this->options['fontsize'],
					0,
					$this->options['font'],
					$this->options['headertext'],
					array()
				);
			list($headerrowwidth, $headerrowheight) = $this->widthAndHeight($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly);
			$this->height += $headerrowheight + $this->options['spacing'] + 2*$this->options['padding'];
		}
		/////// HEADER ROW
				
		$this->_calculateSizes();
		
		if( count($this->data) > 0 )
		{
			$titlewidth  = $this->width - (count($this->options['fields'])*$this->options['spacing']);
			$titlewidth -= $this->options['spacing'];
			$titlewidth -= 2*count($this->options['fields'])*$this->options['padding'];
			foreach($this->options['fields'] as $field => $options)
			{
				if( $field != 'title' && $field != 'description' )
					$titlewidth -= $this->data[1]['width'][$field];
			}
		}
		$this->width  += 2 * $this->options['border'];
		$this->height += 2 * $this->options['border'];
		$this->height += $this->options['spacing'];
		
		$this->im = imagecreate($this->width, $this->height);
		$this->_convertColors();
		
		for($i=0; $i<$this->options['border']; $i++)
		{
			imagerectangle($this->im, $i, $i, $this->width-1-$i, $this->height-1-$i, $this->options['colors']['border'] );
		}
		imagefilledrectangle($this->im, $this->options['border'], $this->options['border'], $this->width-1-$this->options['border'], $this->height-1-$this->options['border'], $this->options['colors']['bg'] );
		$this->x = $this->options['border'];
		$this->y = $this->options['border'];
		
		if( $this->options['headertext'] !== false && !empty($this->options['headertext']) )
			$this->addRow($this->options['headertext'], $headerrowwidth, $headerrowheight, $this->options['headeralign']);

		$i = 0;
		foreach($this->data as $track)
		{
			$stretched = isset($track['width']['title']) ? 'title' : 'description';
			$track['width'][$stretched] = $titlewidth;
			$this->addTrack($track);
			if(++$i>=$this->options['show']) break;
		}
		if( empty($this->data) )
			$this->addRow($msg, $msgwidth, $msgheight, $this->options['erroralign']);
		if( $this->options['urlalign'] !== false && !empty($this->options['urlalign']) )
			$this->addRow($url, $urlwidth, $urlheight, $this->options['urlalign']);
	}
	
	function addTrack($track)
	{			
		$altbg = $this->altbg;
		foreach($this->options['fields'] as $field => $options)
		{
		   $y = $this->addCell($track, $field);
		}
		$this->y = $y;
		$this->x = $this->options['border'];
		if( $this->options['bgstyle'] == ALT_COLUMN )
			$this->altbg = $altbg;
		else
			$this->altbg = !$altbg;
	}
	
	function addRow($text, $width, $height, $align = false)
	{
		$align = $align===false ? $this->options['textalign'] : $align;
		if( $align == 'right' )
			$tx = $this->width - $width - $this->options['padding'] - $this->options['border'] - $this->options['spacing'];
		elseif( $align == 'left' )
			$tx = $this->x + $this->options['spacing'] + $this->options['padding'];
		else
			$tx = round($this->width/2 - $width/2);
		$ty = $this->y + $height + $this->options['spacing'] + $this->options['padding'];
		
		$boxendx = $this->width-$this->options['border']-$this->options['spacing']-1;
		$boxendy = $this->y + $height + $this->options['padding']*2 + $this->options['spacing']-1;

		imagefilledrectangle($this->im, $this->x+$this->options['spacing'], $this->y+$this->options['spacing'], $boxendx, $boxendy, $this->altbg?$this->options['colors']['bg1']:$this->options['colors']['bg2'] );
		
		$color = $this->options['colors']['text'];
		if( !$this->options['antialias'] )
			$color = 0-$color;
		imagefttext($this->im,
			$this->options['fontsize'],
			0, $tx, $ty,
			$color,
			$this->options['font'],
			$text,
			array()
		);
		$this->y = $boxendy+1;
		if( $this->options['bgstyle'] == ALT_ROW || $this->options['bgstyle'] == ALT_CELL )
			$this->altbg = !$this->altbg;
	}
	
	function addCell($track, $name)
	{
		global $feed_type;
					
		list($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly) =
			imageftbbox(
				isset($this->options['fields'][$name]['fontsize']) ? $this->options['fields'][$name]['fontsize'] : $this->options['fontsize'],
				0,
				isset($this->options['fields'][$name]['font']) ? $this->options['fields'][$name]['font'] : $this->options['font'],
				$track[$name],
				array()
			);
		list($width, $height) = $this->widthAndHeight($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly);
		
		$boxendx = $this->x+$track['width'][$name] + $this->options['spacing'] + $this->options['padding']*2 - 1;
		$boxendy = $this->y+$track['height'][$name] + $this->options['spacing'] + $this->options['padding']*2 - 1;

		if( $this->options['fields'][$name]['align'] == 'center' )
		{
			$alt = $this->options['padding'] + floor(($track['width'][$name]-$width)/2);
			if( $width-1+$this->options['spacing'] > $track['width'][$name] )
				$alt = $this->options['padding'] - 1;
			$tx = $this->x + $this->options['spacing'] + $alt;
		}
		elseif( $this->options['fields'][$name]['align'] == 'right' )
			$tx = $boxendx - $width - $this->options['padding'] - $this->options['spacing'];
		else
			$tx = $this->x + $this->options['padding'] + $this->options['spacing'];

		$ty = $this->y + $this->options['spacing'] + $this->options['padding'] + $track['height'][$name] - 1;
		imagefilledrectangle($this->im, $this->x+$this->options['spacing'], $this->y+$this->options['spacing'], $boxendx, $boxendy, $this->altbg?$this->options['colors']['bg1']:$this->options['colors']['bg2'] );

		if( $name == 'description' && isset($track['artist']) && isset($track['title']) && $feed_type == READ_XML_FEED )
		{
			$color = isset($this->options['colors']['artist']) ? $this->options['colors']['artist'] : $this->options['colors']['text'];
			if( !$this->options['antialias'] )
				$color = 0-$color;
			imagefttext($this->im,
				isset($this->options['fields'][$name]['fontsize']) ? $this->options['fields'][$name]['fontsize'] : $this->options['fontsize'],
				0, $tx, $ty,
				$color,
				isset($this->options['fields'][$name]['font']) ? $this->options['fields'][$name]['font'] : $this->options['font'],
				$track['artist'],
				array()
			);
			list($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly) =
				imageftbbox(
					isset($this->options['fields'][$name]['fontsize']) ? $this->options['fields'][$name]['fontsize'] : $this->options['fontsize'],
					0,
					isset($this->options['fields'][$name]['font']) ? $this->options['fields'][$name]['font'] : $this->options['font'],
					$track['artist'],
					array()
				);
			list($width,) = $this->widthAndHeight($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly);
			$tx += $width + 2;
			$track[$name] = ' - '.$track['title'];
			$this->options['colors'][$name] = isset($this->options['colors']['title']) ? $this->options['colors']['title'] : $this->options['colors']['text'];
		}
		
		$color = isset($this->options['colors'][$name]) ? $this->options['colors'][$name] : $this->options['colors']['text'];
		if( !$this->options['antialias'] )
			$color = 0-$color;
		imagefttext($this->im,
			isset($this->options['fields'][$name]['fontsize']) ? $this->options['fields'][$name]['fontsize'] : $this->options['fontsize'],
			0, $tx, $ty,
			$color,
			isset($this->options['fields'][$name]['font']) ? $this->options['fields'][$name]['font'] : $this->options['font'],
			$track[$name],
			array()
		);
		//imagefilledrectangle($this->im, $boxendx-$this->options['padding']+1, $boxendy-$track['height'][$name]-2*$this->options['padding']+1, $boxendx, $boxendy, $this->altbg?$this->options['colors']['bg1']:$this->options['colors']['bg2'] );
		if( $this->options['padding'] > 0 )
			imagefilledrectangle($this->im, $boxendx+1, $boxendy-$track['height'][$name]-2*$this->options['padding']+1, $boxendx+$this->options['spacing'], $boxendy, $this->options['colors']['bg'] );//$this->altbg?$this->options['colors']['bg1']:$this->options['colors']['bg2'] );

		$this->x = $boxendx+1;
		if( $this->options['bgstyle'] == ALT_COLUMN || $this->options['bgstyle'] == ALT_CELL )
			$this->altbg = !$this->altbg;
		return $boxendy+1;
	}
	
	function widthAndHeight($tlx, $tly, $trx, $try, $brx, $bry, $blx, $bly)
	{
		$width = abs($trx) - $tlx; // distance from left to right
		$height = abs($bry) - $try; // distance from top to bottom
		//echo "$trx - $tlx : $bry - $try<br>";
		return array($width, $height);
	}
}

function startElement($xp, $name, $attr)
{
	$GLOBALS['rpi_ot'] = isset($GLOBALS['rpi_ot']) ? $GLOBALS['rpi_ot'] . '/'.$name : '/'.$name;

	if( $GLOBALS['rpi_ot'] == '/RDF:RDF/ITEM' )
	{
		if( !isset($GLOBALS['rpi_tracks']) ) {
			$GLOBALS['rpi_tracks'] = array();
			$GLOBALS['rpi_cur'] = 1;
		}
		else $GLOBALS['rpi_cur']++;
		$GLOBALS['rpi_tracks'][$GLOBALS['rpi_cur']] = array('num'=>$GLOBALS['rpi_cur']); //might get rid of ID
	}
}

//I'm sure I could code this in less lines... but I just hacked this together and it works.
function parseDate($date)
{
	global $timezone, $timezone_alt;
	$day = intval(substr($date, 8, 2));
	$month = intval(substr($date, 5, 2));
	$time = substr($date, 11, 8);
	list($hours, $minutes, $seconds) = explode(':', $time);
	$hours = intval($hours) + $timezone_alt;
	if( $hours < 0 ) {
		$day--;
		if( $day < 0 ) {
			switch($month) {
				case 3: // the month after feb
					$day = ( intval(substr($day, 0, 4)) % 4 == 0 ) ?  29 : 28;
				break;
				case 10: case 5: case 7: case 12: $day = 30; break;
				default: $day = 31; break;
			}
		}
	}
	elseif( $hours > 23 )
	{
		switch($month) {
			case 2: // the month after feb
				$days = ( intval(substr($day, 0, 4)) % 4 == 0 ) ?  29 : 28;
			break;
			case 9: case 4: case 6: case 11: $days = 30; break;
			default: $days = 31; break;
		}
		$day++;
		if( $day > $days ) $day = 0;
	}
	if( $hours < 0 ) $hours = 24 + $hours;
	if( $hours > 23 ) $hours = $hours - 24;
	$day   = $day   < 10?'0'.$day  :$day;
	$month = $month < 10?'0'.$month:$month;
	$hours = $hours < 10?'0'.$hours:$hours;
	return $day .'/'. $month .' @ '. $hours.':'.$minutes.':'.$seconds . (strlen($timezone)<1?'':' ' . $timezone);
}

function endElement($xp, $name)
{
	$GLOBALS['rpi_ot'] = preg_replace('/\/'.$name.'$/', '', $GLOBALS['rpi_ot']);
}

function cdataHandler($xp, $cdata)
{
	switch($GLOBALS['rpi_ot'])
	{
		case '/RDF:RDF/ITEM/DC:TITLE':
			if( !isset($GLOBALS['rpi_tracks'][$GLOBALS['rpi_cur']]['title']) )
				$GLOBALS['rpi_tracks'][$GLOBALS['rpi_cur']]['title'] = '';
			$GLOBALS['rpi_tracks'][$GLOBALS['rpi_cur']]['title'] .= html_entity_decode($cdata, ENT_QUOTES);
		break;
		case '/RDF:RDF/ITEM/MM:ARTIST/DC:CREATOR/DC:TITLE':
			if( !isset($GLOBALS['rpi_tracks'][$GLOBALS['rpi_cur']]['artist']) )
				$GLOBALS['rpi_tracks'][$GLOBALS['rpi_cur']]['artist'] = '';
			$GLOBALS['rpi_tracks'][$GLOBALS['rpi_cur']]['artist'] .= html_entity_decode($cdata, ENT_QUOTES);
		break;
		case '/RDF:RDF/ITEM/DESCRIPTION':
			if( !isset($GLOBALS['rpi_tracks'][$GLOBALS['rpi_cur']]['description']) )
				$GLOBALS['rpi_tracks'][$GLOBALS['rpi_cur']]['description'] = '';
			$GLOBALS['rpi_tracks'][$GLOBALS['rpi_cur']]['description'] .=  html_entity_decode($cdata, ENT_QUOTES);
		break;
		case '/RDF:RDF/ITEM/DC:DATE':
			$GLOBALS['rpi_tracks'][$GLOBALS['rpi_cur']]['date'] = parseDate($cdata);
		break;
	}
}

//u, username
//
function fetchArguments(&$options, $allowed_args = false)
{
	global $user, $timezone, $timezone_alt, $cache_filename, $feed_type;
	$args = is_array($allowed_args) ? $allowed_args : array(
		'ft' => 'feed_type',
		'u'        => "user",
		'user'     => "user",
		'username' => "user",
		'fs'       => "options['fontsize']",
		'fontsize' => "options['fontsize']",
		's'    => "options['show']",
		'show' => "options['show']",
		'cs'      => "options['spacing']",
		'spacing' => "options['spacing']",
		'cp'      => "options['padding']",
		'padding' => "options['padding']",
		'b'      => "options['border']",
		'border' => "options['border']",
		'bc'          => "options['colors']['border']",
		'bordercolor' => "options['colors']['border']",
		'bg'  => "options['colors']['bg']",
		'bg1' => "options['colors']['bg1']",
		'bg2' => "options['colors']['bg2']",
		'artist' => "options['colors']['artist']",
		'ac'     => "options['colors']['artist']",
		
		'text' => "options['colors']['text']",
		'tc'   => "options['colors']['text']",
		'date' => "options['colors']['date']",
		'dc'   => "options['colors']['date']",
		'num' => "options['colors']['num']",
		'nc'   => "options['colors']['num']",
		'title' => "options['colors']['title']",
		'tic'   => "options['colors']['title']",
		
		'timezone' => 'timezone',
		'tz'       => 'timezone',
		'timezone_alt' => 'timezone_alt',
		'tza'          => 'timezone_alt',
		'width' => "options['width']",
		'w'     => "options['width']",
		'header' => "options['headertext']",
		'h'      => "options['headertext']",
		'headeralign' => "options['headeralign']",
		'ha'          => "options['headeralign']",
		'erroralign' => "options['erroralign']",
		'ea'         => "options['erroralign']",
		'url'    => "options['urlalign']"
	);
	$intvals = array(
		'timezone_alt' => true, 'tza' => true,
		'spacing' => true, 'cs' => true,
		'padding' => true, 'cp' => true,
		'border' => true, 'b' => true,
		'show' => true, 's' => true,
		'fontsize' => true, 'fs' => true,
		'width' => true, 'w' => true,
		'ft'=>true
	);
	foreach($args as $arg => $var)
	{
		if( isset($_GET[$arg]) )
		{
			if (get_magic_quotes_gpc())
			   $_GET[$arg] = stripslashes($_GET[$arg]);			
			$b = $_GET[$arg];
			eval("apply_arg(&\${$var}, \$b);");
		}
	}
	if( !preg_match('/^[_a-zA-Z0-9\-\.]{2,15}$/', $user ) ) die('Invalid Username.');
	if( $options['width'] > 1000  || $options['width'] < 300 ) $options['width']=500;
	if( $options['show'] > 10  || $options['show'] < 1 ) $options['show']=10;
	//$cache_filename = $user.'_'.intval($options['show']).'.png';
	$cache_filename = 'rpi-'.$user.((empty($_SERVER["QUERY_STRING"])||$allowed_args===false)?'':'-'.md5($_SERVER["QUERY_STRING"])).'.png';
}
function apply_arg(&$a, $b)
{
	$a = $b;
}

?>

```

You can see it in action (if the bloody server is still working) at [http://www.denness.net/rpi/username/lozzd/.png](http://www.denness.net/rpi/username/lozzd/.png)

Thanks in advance, this is really irratating me now. 

Laurie

---

### Post by intangible on 2005-06-20
My PHP is rusty, and I'm a bit busy today or I'd help you track this down... maybe you should try the programming forum and see if someone there can help.  [http://www.ubuntuforums.org/forumdisplay.php?f=39](http://www.ubuntuforums.org/forumdisplay.php?f=39)  

If you're pretty sure it's the script now, there's lot's of PHP help forums out there too.

---

### Post by lozzd on 2005-06-20
[QUOTE=intangible]My PHP is rusty, and I'm a bit busy today or I'd help you track this down... maybe you should try the programming forum and see if someone there can help.  [http://www.ubuntuforums.org/forumdisplay.php?f=39](http://www.ubuntuforums.org/forumdisplay.php?f=39)  

If you're pretty sure it's the script now, there's lot's of PHP help forums out there too.[/QUOTE]

Ok, thanks for your help! :) Will try posting on some PHP forums.

It just doesnt make any sense that the script worked before, it hasn't been changed, and all of a sudden it doesn't work!?

Thanks again
Laurie

---

### Post by intangible on 2005-06-20
Well, there could be a bug with the script and it only shows up if it is used a certain way.  Did you open up any new features on the site?  Or maybe someone just started using a feature that nobody's been using much before.  There's also the possibility of someone maliciously breaking your site, they may be doing something on purpose (or by accident) that makes your script use more resources than it should.

Either way, having other people take a look at your source code looking for bugs won't hurt. Opensource is good :D.

---

