# MBTA-Bus-1-Activity
Repository of MITxPro Coding Cohort Week 9 Project
___

#Description

## Purpose
Use Massachusetts Bay Transit Authority (MBTA) live data to illustrate active busses on Bus Line #1.

## Background
This project builds on weekly exercises for the MITxPro coding cohort.

The weekly exercises provided the cohort with starter code to create a map using mapbox.

The created map was centered on Cambridge, MA on the MIT campus.

One weekly exercise guided the creation of animated markers using provided coordinates (bust stops between MIT and Harvard). An 'html' button started the animation.

An additional weekly exercise showed how to get live data from the MBTA for the bus lines.

MBTA bus line #1 runs between Nubian Station (formerly Dudley Station) in Boston and Harvard Square in Cambridge. The Cambridge portion of the line runs between MIT and Harvard.

## Project
This project combines the weekly exercises to create a real time bus tracker for MBTA bus #1. Additional review of mapbox features showed how to draw lines on the map and add popups to markers.

Starting with the provided map scaffolding, the following improvements were made:
1. Center was moved to center of Harvard Bridge (center of bus line).
2. Tutorial code from mapbox was modified to draw lines representing the inbound and outbound routes of bus #1.
	a. Tutorial code: https://docs.mapbox.com/mapbox-gl-js/example/geojson-line/
	b. Coordinates from google maps was used to describe the line.
	c. Inbound (to Nubian) is colored green. Outbound (to Harvard) is colored red.
3. Code was added to repeatedly fetch data from the MBTA for bus #1
4. An array of map markers gets created for each batch of data fetched.
	a. Color is set based on the 'attributes.direction_id' (0 = red, 1 = green)
	b. Coordinates are set based on the 'attributes.latitude' and 'attributes.longitude' data.
	c. A popup is bound to each marker.
		i. Bus number is set based on 'attributes.label'.
		ii. Occupancy status is set based on 'attributes.occupancy_status'
		
On load the map is loaded, centered, and provided with an action button.
The map button calls the bus1() which calls the nubianToHarvard() and harvardToNubian() functions (both contained in associated 'busLines.js' file). These draw the lines on the map described in Item 2 above.
The bus1() function then calls the run() function which
1. Fetches the data.
2. Discards (pops()) existing markers.
3. Creates new markers based on (new) data.

## Result
The following files are contained in this repository.
1. Index.html - Main document: Draws map, Fetches data, Controls markers
2. styles.css - Stylesheet for map and popups
3. busLines.js - Defines lines for bus routes

# Installation
The resulting code was tested on Google Chrome. Once loaded, the animation starts by clicking the button.

# Support
For questions contact rmc4th@yahoo.com

# Roadmap
For future revisions, bus line coordinates could be refined and the lines thinned to provide better visual separation. Points could be added for the actual bus stops. Logic could be added to adjust for busses coming off service (driving to bus yard).

# License Information
This work was done as part of MIT xPRO Professional Certificate in Coding. The code above comes with the following license:

MIT License

Copyright (c) 2020 John Williams

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

For Mapbox

mapbox-gl-js v2.0

Mapbox Web SDK

Copyright (c) 2020, Mapbox

All rights reserved.

Mapbox gl-js version 2.0 or higher (“Mapbox Web SDK”) must be used according to
the Mapbox Terms of Service. This license allows developers with a current active
Mapbox account to use and modify the Mapbox Web SDK. Developers may modify the
Mapbox Web SDK code so long as the modifications do not change or interfere with
marked portions of the code related to billing, accounting, and anonymized data
collection. The Mapbox Web SDK only sends anonymized usage data, which Mapbox uses
for fixing bugs and errors, accounting, and generating aggregated anonymized
statistics. This license terminates automatically if a user no longer has an
active Mapbox account.

For the full license terms, please see the Mapbox Terms of Service at
https://www.mapbox.com/legal/tos/.
