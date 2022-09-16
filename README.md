# datatable
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Latihan 1</title>
    <link rel="stylesheet" href="DataTables/datatables.min.css">
    <title>contoh</title>
    <style>
        #simpan{
            padding: 10px;
            width:100%;
            background: linear-gradient( #2d7e77, #139a8f );
            border-radius: 10px;
            color: #fff;
            border-width: 0px;
        }
        #simpan:hover{
            color: #000;
            background: linear-gradient( #2d7e77, #139a8f );
        }
    </style>
</head>
<body>
    <input type="hidden" id="id" autocomplete="off">
    <table width="50%" align="center">
        <tr>
            <td colspan="4" align="center"><h3> Input Data Ke Tabel</h3></td>
            </tr>
            <tr>
    <td>Nama</td>
    <td><input style="width:90%; padding:5px;border-radius:10px" type="text" name="nama" placeholder="masukan nama" /></td>
    <td>Kelas</td>
    <td><input style="width:90%; padding:5px;border-radius:10px" type="text" name="kelas" placeholder="masukan kelas" /></td>
            </tr>
            <tr>
    <td>Alamat</td>
    <td><input style="width:90%; padding:5px;border-radius:10px" type="text" name="alamat" placeholder="masukan alamat" /></td>
    <td>Nohp</td>
    <td><input style="width:90%; padding:5px;border-radius:10px" type="text" name="nohp" placeholder="masukan nohp" /></td>
            </tr>
            <tr>
                <td colspan="2"><button id="simpan">simpan data</button></td>
                <td colspan="2"><button id="hapus" style="display:none; padding:10px; background-color: red; color:white;">hapus data</button></td>
            </tr>
            </table>
    <table id="table" class="table">
        <thead>
            <tr>
                <th width="1%">No</th>
                <th width="5%">Nama</th>
                <th width="10%">Kelas</th>
                <th width="15%">alamat</th>
                <th width="20%">no hp</th>
            </tr>
        </thead>
    </table>
    <script src="DataTables/jQuery-3.6.0/jQuery-3.6.0.min.js"></script>
    <script src="DataTables/datatables.min.js"></script>
    <script>
        var tabel = $("#table").DataTable({
            responsive: true,
            select: true  
                    });
            tabel.on('select', function(){
                $("#id").val(tabel.rows(".selected").data().toArray()[0][0])
             $("input[name=nama").val(tabel.rows(".selected").data().toArray()[0][1]);
             $("input[name=kelas").val(tabel.rows(".selected").data().toArray()[0][2]);
             $("input[name=alamat").val(tabel.rows(".selected").data().toArray()[0][3]);
             $("input[name=nohp").val(tabel.rows(".selected").data().toArray()[0][4]);
             $("#simpan").html("ubah data");
             $("#hapus").show();
            });

            tabel.on('deselect', function(){
                $("#simpan").html("simpan data");
                $("input[name=nama").val(null);
                $("input[name=kelas").val(null);
                $("input[name=alamat").val(null);
                $("input[name=nohp").val(null);
                $("#id").val(null);
                $("#haous").hide();
            });
        var no = 1;
        $("#simpan").click(function(){
            var nama = $("input[name=nama").val();
            var kelas = $("input[name=kelas").val();
            var alamat = $("input[name=alamat").val();
            var nohp = $("input[name=nohp").val();
            var id =$("#id").val();

            if(id.length > 0){
                tabel.row(id-1).data(
                    [id,nama,kelas,alamat,nohp]
                ).draw(false);
            }else{
            tabel.row.add(
                [ no,nama,kelas,alamat,nohp ]
                ).draw(false);
                no++
            }
             $("#simpan").html("simpan data");
             $("input[name=nama").val(null);
             $("input[name=kelas").val(null);
             $("input[name=alamat").val(null);
             $("input[name=nohp").val(null);
             $("#id").val(null);
            });
            </script>
</body>
</html>
