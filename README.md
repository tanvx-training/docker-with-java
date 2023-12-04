# Docker

## Tài Nguyên Quan Trọng Cần Đọc Trước Hướng Dẫn Docker:

[Giới thiệu dễ hiểu về containers, VMs và Docker](https://medium.com/free-code-camp/a-beginner-friendly-introduction-to-containers-vms-and-docker-79a9e3e119b)

[Hướng dẫn Docker với Python](https://medium.com/hackernoon/docker-tutorial-getting-started-with-python-redis-and-nginx-81a9d740d091)

************************************

## **Tại sao sử dụng DOCKER?**

- Một ứng dụng hoạt động tốt trên bảng điều khiển của nhà phát triển nhưng không chạy đúng trong quá trình kiểm thử hoặc sản xuất.

- Trong môi trường phát triển, có thể có một phần mềm đã được cập nhật, nhưng trong quá trình kiểm thử và sản xuất, một phiên bản cũ đang được sử dụng.

- Docker là một chương trình/môi trường máy tính giúp triển khai và chạy ứng dụng một cách dễ dàng bằng cách sử dụng một khái niệm được biết đến là "containerization" (đóng gói ứng dụng vào container).

- Hãy tưởng tượng, như một nhà phát triển, ứng dụng của bạn được đóng gói với tất cả các thành phần cần thiết và được vận chuyển như một gói duy nhất.

- Docker, nói cách khác, là một công cụ ảo hóa nhẹ và nền tảng container nơi bạn có thể chạy và triển khai ứng dụng và các phụ thuộc của nó có thể chạy trong môi trường Linux.

- Docker là một dự án mã nguồn mở dựa trên container Linux. Nó sử dụng các tính năng của Kernel Linux như các không gian tên và các nhóm kiểm soát để tạo ra các container trên cơ sở hệ điều hành.

## **Docker Engine**

- Docker Engine là tầng trung tâm trên đó Docker chạy. Đây là một công cụ chạy nhẹ và tầng công nghệ quản lý container, hình ảnh, quá trình xây dựng, và nhiều tính năng khác. Nó chạy một cách tự nhiên trên các hệ thống Linux và bao gồm:
  1. Một Docker Daemon chạy trên máy tính máy chủ.
  2. Một Docker Client sau đó tương tác với Docker Daemon để thực hiện các lệnh.
  3. Một REST API để tương tác từ xa với Docker Daemon.

## **Docker Client**

- Docker Client là điều bạn, như người dùng cuối cùng của Docker, tương tác với. Hãy tưởng tượng đó như là giao diện người dùng (UI) cho Docker.

## **Docker Daemon**

- Docker Daemon là cái thực sự thực hiện lệnh được gửi đến Docker Client — như xây dựng, chạy, và phân phối các container của bạn. 
- Docker Daemon chạy trên máy tính máy chủ, nhưng như một người sử dụng, bạn không bao giờ tương tác trực tiếp với Daemon. 
- Docker Client cũng có thể chạy trên máy tính máy chủ, nhưng điều này không bắt buộc. Nó có thể chạy trên một máy tính khác và tương tác với Docker Daemon đang chạy trên máy tính máy chủ.

## **Volumes**

- Volumes là "dữ liệu" của một container, được khởi tạo khi một container được tạo. 
- Volumes cho phép bạn lưu trữ và chia sẻ dữ liệu của container. Dữ liệu volumes là riêng biệt với Hệ thống tệp hợp mặc định và tồn tại dưới dạng thư mục và tệp thông thường trên hệ thống tệp của máy chủ. Vì vậy, ngay cả khi bạn xóa, cập nhật hoặc xây dựng lại
container, volumes dữ liệu sẽ vẫn giữ nguyên. 
- Khi bạn muốn cập nhật một volume, bạn thay đổi trực tiếp vào nó. (Như một điều thêm vào, volumes dữ liệu có thể được chia sẻ và sử dụng lại giữa nhiều container, điều này khá tuyệt vời.)

## **Kiến trúc Microservices:**

- Ý tưởng đằng sau kiến trúc microservices là một số ứng dụng dễ xây dựng và bảo trì hơn khi được phân chia thành các phần nhỏ hơn.

- Mỗi thành phần được phát triển riêng biệt và thực hiện....

- Ví dụ: Dịch vụ Mua sắm trực tuyến:
  + Dịch vụ Tài khoản
  + Danh mục Sản phẩm
  + Máy chủ Giỏ hàng
  + Máy chủ Đặt hàng

## **Ưu điểm của kiến trúc microservices:**

- Dễ xây dựng và bảo trì do được phân chia thành các phần nhỏ.
- Nếu chúng ta cần một số tính năng mới hoặc cập nhật trong một module, nó dễ dàng hơn vì sẽ ít phụ thuộc so với ứng dụng như một tổng thể.
- Nếu một thành phần nào đó gặp sự cố, ứng dụng sẽ không bị ảnh hưởng nhiều.

## **Vấn đề khi áp dụng kiến trúc microservices:**

- Trước Docker: Đối với kiến trúc microservices, chúng ta có một máy chủ và có nhiều máy ảo (VMs), mỗi máy ảo là một dịch vụ micro. Vấn đề ở đây là sự lãng phí tài nguyên nhiều.
Khi chúng ta sử dụng nhiều VM hơn cho các ứng dụng lớn hơn, nhiều không gian đĩa, RAM sẽ không được sử dụng.

## **Làm thế nào Docker giải quyết vấn đề này:**

- Chúng ta có thể chạy nhiều dịch vụ micro trên một máy ảo bằng cách chạy các container Docker khác nhau cho mỗi dịch vụ micro.
- Docker không cần bất kỳ yêu cầu RAM, ổ đĩa nào ban đầu.

## **Làm thế nào Docker giải quyết vấn đề "không có môi trường tính toán nhất quán trong quá trình triển khai (phát triển, kiểm thử, sản xuất)":**

- Các container Docker được phát triển bởi các nhà phát triển.
- Docker cung cấp một môi trường tính toán nhất quán suốt toàn bộ chu kỳ phát triển phần mềm (SDLC).

## **Image là gì?**
- Docker image là cơ sở của container. Nó là một bộ sưu tập của các lớp được xếp chồng lên nhau. Mỗi Docker image tham chiếu đến một danh sách các lớp chỉ đọc được biểu diễn sự khác biệt trong hệ thống tệp. Hãy nghĩ về nó giống như tệp jar cho ứng dụng Java, bạn tạo một tệp jar nhưng bạn có thể triển khai nó ở bất kỳ đâu mà một thời gian chạy Java được bật.
- Một Docker image là một bản lưu trữ chứa tất cả các tệp cần thiết cho một container.
- Bạn có thể tạo nhiều container Docker từ cùng một hình ảnh Docker.
- Hình ảnh sau đó có thể được triển khai vào bất kỳ môi trường Docker nào và thực thi như một container.
- Một Docker image chứa tất cả mọi thứ cần thiết để chạy một ứng dụng như một container. Điều này bao gồm:
    - mã nguồn
    - thời gian chạy
    - thư viện
    - biến môi trường
    - tệp cấu hình

  ![docker image](https://github.com/Tikam02/DevOps-Guide/blob/master/img/container-layers.jpg)
- 
## Định Nghĩa Về Container

- **Container là gì?**
  + Container là một đơn vị tiêu chuẩn của phần mềm, đóng gói mã nguồn và tất cả các phụ thuộc của nó để ứng dụng chạy nhanh chóng và đáng tin cậy từ một môi trường máy tính này sang môi trường máy tính khác.

  + Một hình ảnh container Docker là một gói phần mềm nhẹ, độc lập, có thể thực thi chứa mọi thứ cần thiết để chạy một ứng dụng: mã nguồn, thư viện, cài đặt và v.v.

  + Hình ảnh container trở thành container khi chạy và trong trường hợp của container Docker, hình ảnh trở thành container khi chúng chạy trên Docker engine.

  + Container chia sẻ kernel hệ điều hành của máy và do đó không yêu cầu một hệ điều hành cho mỗi ứng dụng.

  + Ứng dụng an toàn hơn trong container và Docker cung cấp khả năng cách ly mạnh mẽ nhất trong ngành công nghiệp.

  + Container Docker là một phần thực sự được tạo ra từ một hình ảnh Docker. Sự khác biệt duy nhất giữa một hình ảnh Docker và một container Docker là một lớp ghi có thể ghi ở đỉnh. Khi bạn tạo ra một container mới, bạn thêm một lớp ghi mỏng mới ở đỉnh của ngăn xếp cơ sở. Lớp này thường được gọi là "lớp container". Tất cả các thay đổi được thực hiện trên container đang chạy — như viết tệp tin mới, sửa đổi tệp tin hiện tại và xóa tệp tin — đều được ghi vào lớp container ghi mỏng này. Nhưng một khi bạn xóa container, lớp trên cùng này cũng sẽ bị xóa. Vì vậy, nó không bền. Điều tốt nhất với Docker là bạn có thể tạo một hình ảnh Docker bằng cách sử dụng container Docker hiện tại với một lệnh commit. Do đó, cho phép chúng ta ghi lại thông tin hệ thống và làm cho nó không thể thay đổi để có thể sao chép ở bất kỳ đâu. Điều này giải quyết nhiều vấn đề liên quan đến máy chủ mà chúng ta gặp phải ngày nay.

    ![Container Docker](https://github.com/Tikam02/DevOps-Guide/blob/master/img/docker-image.png)

## Containers So Với Máy Ảo (VM)

- **Khi nói về containerization, thường so sánh với máy ảo. Hãy xem xét hình ảnh sau để thấy sự khác biệt chính:**

    - Nền tảng container Docker luôn chạy trên hệ điều hành máy chủ. Container chứa bản bin, thư viện và ứng dụng. Container không chứa hệ điều hành khách, điều này đảm bảo rằng container là nhẹ.

    - Ngược lại, máy ảo chạy trên một trình ảo hóa và bao gồm hệ điều hành khách của riêng nó. Điều này làm tăng kích thước của máy ảo đáng kể, làm cho thiết lập máy ảo phức tạp hơn và yêu cầu nhiều tài nguyên hơn để chạy mỗi máy ảo.

  ![Container vs VM](https://github.com/Tikam02/DevOps-Guide/blob/master/img/dockervsvm.png)

## Dockerfile

- **Dockerfile là gì?**
    - Bản thiết kế của một hình ảnh Docker (một tài liệu văn bản) được gọi là Dockerfile. Tệp này chứa tất cả các lệnh bạn sẽ chạy để xây dựng hình ảnh Docker bạn muốn. Docker có thể xây dựng hình ảnh bằng cách đọc tệp này, điều này là một trong những ưu điểm chính của Docker.

    - Ví dụ đơn giản của một Dockerfile:

    ```bash
    # Ví dụ siêu đơn giản của một Dockerfile
    FROM ubuntu:latest
    MAINTAINER Tikam Alma 

    RUN apt-get update
    RUN apt-get install -y python python-pip wget
    RUN pip install Flask

    ADD hello.py /home/hello.py

    WORKDIR /home
    ```

    - Đầu tiên, chúng ta viết một Dockerfile, giống như định nghĩa của hình ảnh. Sử dụng Dockerfile, chúng ta tạo ra một hình ảnh Docker. Sau đó, chúng ta đẩy hình ảnh này lên Docker Hub và cung cấp một thẻ duy nhất có thể được sử dụng để xác định hình ảnh của chúng tôi. Bằng cách sử dụng thẻ và tên hình ảnh này, chúng ta có thể kéo hình ảnh Docker và triển khai trên máy tính khác dưới dạng container Docker.

## Hoạt Động Chi Tiết Của Containers

* Thuật ngữ "container" thực sự chỉ là một khái niệm trừu tượng

để mô tả cách một số tính năng khác nhau làm việc cùng nhau để hình dung một "container". Hãy đi sâu vào chúng một cách nhanh chóng:

- **1) Namespaces**
    - Namespaces cung cấp cho container một cái nhìn riêng của hệ điều hành Linux cơ bản, giới hạn điều container có thể nhìn thấy và truy cập. Khi bạn chạy một container, Docker tạo ra các namespaces mà container cụ thể sẽ sử dụng.

    - Có nhiều loại namespaces khác nhau trong một kernel mà Docker sử dụng, ví dụ:

        - a. NET: Cung cấp cho container cái nhìn riêng của nền tảng mạng của hệ thống (ví dụ: thiết bị mạng riêng của container, địa chỉ IP, bảng định tuyến IP, thư mục /proc/net, số cổng, v.v.).

        - b. PID: PID là viết tắt của Process ID. Nếu bạn đã bao giờ chạy `ps aux` trong dòng lệnh để kiểm tra quá trình nào đang chạy trên hệ thống của bạn, bạn sẽ thấy một cột có tên là "PID". Namespace PID cung cấp cho container cái nhìn được phân loại riêng của chúng về các quá trình mà chúng có thể xem và tương tác, bao gồm một quá trình init độc lập (PID 1), đó là "tổ tiên của tất cả các quá trình".

        - c. MNT: Đưa cho container cái nhìn riêng của các "mount" trên hệ thống. Do đó, các quá trình trong các không gian mount khác nhau có cái nhìn khác nhau về cấu trúc thư mục hệ thống tệp.

        - d. UTS: UTS viết tắt của UNIX Timesharing System. Nó cho phép một quá trình xác định các định danh hệ thống (ví dụ: tên máy chủ, tên miền, v.v.). UTS cho phép container có tên máy chủ và tên miền NIS riêng biệt không phụ thuộc vào các container và hệ thống máy chủ khác.

        - e. IPC: IPC viết tắt của InterProcess Communication. Namespace IPC có trách nhiệm cách ly tài nguyên IPC giữa các quá trình chạy trong từng container.

        - f. USER: Namespace này được sử dụng để cách ly người dùng trong mỗi container. Nó hoạt động bằng cách cho phép container có cái nhìn khác về phạm vi uid (user ID) và gid (group ID) so với hệ thống máy chủ. Kết quả là, uid và gid của một quá trình có thể khác nhau bên trong và bên ngoài một không gian người dùng, điều này cũng cho phép một quá trình có một người dùng không đặc quyền bên ngoài một container mà không cần phải hi sinh đặc quyền root bên trong một container.

- **2) Control groups**
    - Control groups (còn được gọi là cgroups) là một tính năng của kernel Linux giúp cách ly, ưu tiên và tính toán việc sử dụng tài nguyên (CPU, bộ nhớ, đọc/ghi I/O ổ đĩa, mạng, v.v.) của một tập hợp các quá trình. Một cgroup đảm bảo rằng các container Docker chỉ sử dụng các tài nguyên mà chúng cần — và nếu cần, thiết lập giới hạn cho tài nguyên mà một container *có thể* sử dụng. Cgroups cũng đảm bảo rằng một container đơn lẻ không làm cạn kiệt một trong những tài nguyên đó và làm cho toàn bộ hệ thống đổ bể.

- **3) Hệ thống tệp hợp nhất độc lập:**
    - Docker sử dụng Hệ thống tệp hợp nhất để xây dựng hình ảnh. Bạn có thể nghĩ về Hệ thống tệp hợp nhất như một hệ thống tệp chồng, có nghĩa là tệp và thư mục của các hệ thống tệp tách biệt (được biết đến là nhánh) có thể được chồng lên nhau một cách trong suốt để tạo thành một hệ thống tệp duy nhất.

    - Nội dung của các thư mục có cùng đường dẫn trong các nhánh chồng lên nhau được xem như một thư mục duy nhất được hợp nhất, điều này loại bỏ cần phải tạo ra bản sao riêng lẻ của mỗi lớp. Thay vào đó, chúng có thể đều được chỉ đến cùng một tài nguyên; khi các lớp cần được sửa đổi, nó sẽ tạo ra một bản sao và sửa đổi một bản sao cục bộ, giữ nguyên bản gốc không thay đổi. Đó là cách hệ thống tệp có thể *trông giống như* có thể ghi được mà không cần thực sự cho phép ghi. (Nói cách khác, đó là một hệ thống "ghi vào khi cần.")

    - Hệ thống có lớp mang lại hai lợi ích chính:
  
      + Không sao chép: các lớp giúp tránh việc sao chép một bộ tệp hoàn chỉnh mỗi khi bạn sử dụng một hình ảnh để tạo và chạy một container mới, làm cho quá trình khởi tạo container Docker trở nên rất nhanh chóng và giá rẻ.
      + Phân chia lớp: Việc thay đổi trở nên nhanh chóng hơn — khi bạn thay đổi một hình ảnh, Docker chỉ truyền đạt các cập nhật đến lớp đã được thay đổi.

