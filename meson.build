project('caps2esc', 'c',
	version : '1.0.3',
	license : 'GPL-3.0',
	default_options : ['c_std=c99'])

executable(meson.project_name(), meson.project_name() + '.c',
	c_args : '-D_POSIX_C_SOURCE',
	dependencies : [dependency('libevdev'), dependency('libudev')],
	install : true)

unit = meson.project_name() + '.service'
path = join_paths(get_option('prefix'), get_option('bindir'))
custom_target('systemd',
	output : unit,
	input : unit,
	command : [find_program('sed'), '-n',
		'-e', 's:@PATH@:' + path + ':g',
		'-e', 'w @OUTPUT@', '@INPUT@'],
	install : true,
	install_dir : '/etc/systemd/system')
