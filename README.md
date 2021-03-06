pyflightdata
============

[![Travis](https://img.shields.io/travis/supercoderz/pyflightdata.svg?maxAge=2592000)]()
[![PyPI](https://img.shields.io/pypi/dw/pyflightdata.svg?maxAge=2592000)]()
[![PyPI](https://img.shields.io/pypi/v/pyflightdata.svg?maxAge=2592000)]()
[![PyPI](https://img.shields.io/pypi/pyversions/pyflightdata.svg?maxAge=2592000)]()

A simple library to get flight data from flightradar24 from within Python code.

Please note that this is not an offical API and does not use any undocumented API from flightradar24.
This code simply automates what you would do from a browser and extracts the flight history by aircraft registration or by the flight number. 

We depend on the structure of the pages, so if the pages change, then this API will need to be updated. There is no defined plan to look out for these changes and keep the API updated. So do not use this in mission critical applications.

The idea is to use this in cases where you want to exatract flight information for analysis, in a reasonable manner without bombarding the site with lot of requests and without having to manually do the recording of data by hand. Or when you have an application were you would like to give the user the ability to search from flight information and see within the app

The API does not provide any mass request mechanism and does not recommend such usage or take responsibility for any such usage by anyone.

Eventually we will add more sites and more information to the API.


IPython notebook example
========================

Here are a few basic examples

http://nbviewer.jupyter.org/github/supercoderz/pyflightdata/blob/master/pyflightdata%20examples.ipynb

Installation and Usage
======================

You can install with ``pip``

    pip install pyflightdata

Usage is very simple. To get the list of all countries with airports use ``get_countries``

    get_countries()
	
To get list of all airports and the airport codes in a given country use ``get_airports``

    get_airports('India')
	
This will return a list of (name,code) tuples.

To get information on a particular aircraft, use ``get_info_by_tail_number``

    get_info_by_tail_number('VT-ALL')
	
This will return a dict.

To get flight history, you can use tail number or flight number. Both will return a list of dicts with the details of date of flight, from and to, tail number or flight, status and arrival departure times. The commands are

    get_history_by_flight_number('AI101')
	
or

    get_history_by_tail_number('VT-ALL')
	
There are methods that you can use to get the list of all the airlines, their fleet list and list of all flight numbers

    get_airlines()
	
This returns a list of dicts. Each airline dict has a field called 'key' which can be used to get the fleet and flight numbers

    get_fleet('air-india-aic')
	
    get_flights('air-india-aic')