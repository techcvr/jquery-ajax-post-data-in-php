# jquery ajax post data in php
### post php data using jquery 


## HTML Code
```html
<input type="text" id="school_fk" value="1"/>

<select class="form-control" id="language">
  <option value="">Select</option>
  <option value="HN">Hindi</option> 
  <option value="BN">Bengali</option> 
  <option value="EN">English</option> 								
</select>
```



## Jquery Code
```jquery
<script>
$('#language').change(function () {
	var school = $('#school_fk').val();
	var language = $("#language").val();

	$.ajax({
		url:"getQnty.php",
		method:"POST",
		data:{school1:school,language1:language},
		success:function(data){
			$("#quantity").val(data);
		}}
	);
});
</script>
```

## PHP Code
``` php
<?php
include 'connection.php';

$lang = $_POST['language1'];
$school = $_POST['school1'];

$sql1 = "SELECT * FROM `al_volunteers` where `language` = '$lang' and `school_pk` = '$school'";
$res1 = $conn->query($sql1) or die($conn->error);
echo $num = $res1->num_rows;
?>

```
