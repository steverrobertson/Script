% Is there a local command?
on topic local $command_topic
do
	println "Received local command: " | $this_data

	if $this_data = "on" then
		setvar $relay_status = 1
		% setvar $blink = 0
		gpio_out 14 $relay_status
		% gpio_out 13 not ($relay_status)
	else
	    if $this_data = "off" then
		setvar $relay_status = 0
		% setvar $blink = 0
		gpio_out 14 $relay_status
		% gpio_out 13 not ($relay_status)
	    endif
	endif
	% if $this_data = "toggle" then
	%	setvar $relay_status = not ($relay_status)
	%	gpio_out 12 $relay_status
	%	gpio_out 13 not ($relay_status)
	% endif
	% if $this_data = "blink" then
	%	setvar $blink = 1
	%	settimer 1 500
	% endif

	publish local $status_topic $relay_status retained
	publish remote $status_topic $relay_status retained
	
on topic local $Voltage_topic
do
	println "Received local command: " | $this_data

	if $this_data > 54 then
		setvar $relay_status = 1
		% setvar $blink = 0
		gpio_out 14 $relay_status
		% gpio_out 13 not ($relay_status)
	else
	    if $this_data < 52.5 then
		setvar $relay_status = 0
		% setvar $blink = 0
		gpio_out 14 $relay_status
		% gpio_out 13 not ($relay_status)
	    endif
	endif

	publish remote $Voltage_topic $this_data

% The local pushbutton
% on gpio_interrupt 0 pullup
% do
	% println "New state GPIO 0: " | $this_gpio
	% if $this_gpio = 0 then
	%	setvar $blink = 0
	%	publish local $command_topic "toggle"
	% endif


% Blinking
%on timer 1
%do
%	if $blink = 1 then
%		publish local $command_topic "toggle"
%		settimer 1 500
%	endif
