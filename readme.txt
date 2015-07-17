=== Plugin Name ===
Contributors: arnaudban, studio-goliath
Tags: dailymotion, widget, video
Requires at least: 3.5
Tested up to: 4.2.1
Stable tag: trunk
License: GPLv2
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Add widget to display your latest dailymotion videos

== Description ==

Add widget to display your latest dailymotion videos.
Just set your Dailymotion's username and choose the number of videos you'd like to display.

== Frequently Asked Questions ==

= Can it be customisable ? =

Yes there are somes filters that can help you get the output that you want :

the **dlvw_dailymotion_video_fields** filter, that let you filter the video fields to get from dailymotion.
Possible fields can be found here : https://developer.dailymotion.com/documentation#video-fields

Example :
`
function dlvw_dailymotion_video_fields( $fields ){

    array_push($fields, 'duration_formatted');

    return $fields;
}
add_filter( 'dlvw_dailymotion_video_fields', 'dlvw_dailymotion_video_fields' );
`

the **dlvw_dailymotion_video_link** filter, that let you filter the ouput form each video

Example :
`
function dlvw_dailymotion_video_link( $output, $video, $widget_instance ){

    $thumbnail_size = $widget_instance['thumb_size'];
    $thumbnail_src = $video->{$thumbnail_size};


    $output = "<a href='{$video->embed_url}?TB_iframe=true' class='thickbox'>";
    $output .= "<img src='$thumbnail_src' />";
    $output .= "<h3>{$video->title} {$video->duration_formatted}</h3>";
    $output .= '</a>';

    return $output;
}
add_filter( 'dlvw_dailymotion_video_link', 'dlvw_dailymotion_video_link', 10, 3 );



== Screenshots ==

1. Customizer view of the widget
2. Admin view of the widget
3. How the widget displays with the theme TwentyFifteen

== Changelog ==

= 0.1 =
* First version of the plugin
